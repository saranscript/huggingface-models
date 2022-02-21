---
language: en
datasets:
- librispeech_asr
tags:
- audio
- automatic-speech-recognition
license: apache-2.0
widget:
- example_title: Librispeech sample 1
  src: https://cdn-media.huggingface.co/speech_samples/sample1.flac
- example_title: Librispeech sample 2
  src: https://cdn-media.huggingface.co/speech_samples/sample2.flac
---

# Wav2Vec2-Base-960h

This repository is a reimplementation of [official Facebook’s wav2vec](https://huggingface.co/facebook/wav2vec2-base-960h).
There is no description of converting the wav2vec [pretrain model](https://github.com/pytorch/fairseq/tree/master/examples/wav2vec#wav2vec-20) to a pytorch.bin file.
We are rebuilding pytorch.bin from the pretrain model.
Here is the conversion method.

```bash
pip install transformers[sentencepiece]
pip install fairseq -U

git clone https://github.com/huggingface/transformers.git
cp transformers/src/transformers/models/wav2vec2/convert_wav2vec2_original_pytorch_checkpoint_to_pytorch.py .

wget https://dl.fbaipublicfiles.com/fairseq/wav2vec/wav2vec_small_960h.pt -O ./wav2vec_small_960h.pt
mkdir dict
wget https://dl.fbaipublicfiles.com/fairseq/wav2vec/dict.ltr.txt

mkdir outputs
python convert_wav2vec2_original_pytorch_checkpoint_to_pytorch.py --pytorch_dump_folder_path ./outputs --checkpoint_path ./wav2vec_small_960h.pt --dict_path ./dict
```

# Usage

To transcribe audio files the model can be used as a standalone acoustic model as follows:

```python
 from transformers import Wav2Vec2Tokenizer, Wav2Vec2ForCTC
 from datasets import load_dataset
 import soundfile as sf
 import torch
 
 # load model and tokenizer
 tokenizer = Wav2Vec2Tokenizer.from_pretrained("facebook/wav2vec2-base-960h")
 model = Wav2Vec2ForCTC.from_pretrained("facebook/wav2vec2-base-960h")
 
 # define function to read in sound file
 def map_to_array(batch):
     speech, _ = sf.read(batch["file"])
     batch["speech"] = speech
     return batch
     
 # load dummy dataset and read soundfiles
 ds = load_dataset("patrickvonplaten/librispeech_asr_dummy", "clean", split="validation")
 ds = ds.map(map_to_array)
 
 # tokenize
 input_values = tokenizer(ds["speech"][:2], return_tensors="pt", padding="longest").input_values  # Batch size 1
 
 # retrieve logits
 logits = model(input_values).logits
 
 # take argmax and decode
 predicted_ids = torch.argmax(logits, dim=-1)
 transcription = tokenizer.batch_decode(predicted_ids)
 ```
 
 ## Evaluation
 
 This code snippet shows how to evaluate **facebook/wav2vec2-base-960h** on LibriSpeech's "clean" and "other" test data.
 
```python
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Tokenizer
import soundfile as sf
import torch
from jiwer import wer


librispeech_eval = load_dataset("librispeech_asr", "clean", split="test")

model = Wav2Vec2ForCTC.from_pretrained("facebook/wav2vec2-base-960h").to("cuda")
tokenizer = Wav2Vec2Tokenizer.from_pretrained("facebook/wav2vec2-base-960h")

def map_to_array(batch):
    speech, _ = sf.read(batch["file"])
    batch["speech"] = speech
    return batch

librispeech_eval = librispeech_eval.map(map_to_array)

def map_to_pred(batch):
    input_values = tokenizer(batch["speech"], return_tensors="pt", padding="longest").input_values
    with torch.no_grad():
        logits = model(input_values.to("cuda")).logits

    predicted_ids = torch.argmax(logits, dim=-1)
    transcription = tokenizer.batch_decode(predicted_ids)
    batch["transcription"] = transcription
    return batch

result = librispeech_eval.map(map_to_pred, batched=True, batch_size=1, remove_columns=["speech"])

print("WER:", wer(result["text"], result["transcription"]))
```

*Result (WER)*:

| "clean" | "other" |
|---|---|
| 3.4 | 8.6 |


# Reference


[Facebook's Wav2Vec2](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio/)

[Facebook's huggingface Wav2Vec2](https://huggingface.co/facebook/wav2vec2-base-960h)

[Paper](https://arxiv.org/abs/2006.11477)
