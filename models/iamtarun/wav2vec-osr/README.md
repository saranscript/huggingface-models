---
language: en
datasets:
- librispeech_asr
tags:
- audio
- automatic-speech-recognition
- speech to text
license: apache-2.0
widget:
- example_title: OSR sample 1
  src: https://github.com/TheSoundOfAIOSR/rg_speech_to_text/blob/main/data/finetuning-dataset/audiofiles/TA-5.wav?raw=true
- example_title: OSR sample 2
  src: https://github.com/TheSoundOfAIOSR/rg_speech_to_text/blob/main/data/finetuning-dataset/audiofiles/TK-17.wav?raw=true
- example_title: Librispeech sample 1
  src: https://cdn-media.huggingface.co/speech_samples/sample1.flac
- example_title: Librispeech sample 2
  src: https://cdn-media.huggingface.co/speech_samples/sample2.flac
---

# Wav2Vec-OSR
Finetuned facebook's wav2vec2 model for speech to text module of [The Sound Of AI open source research group](https://thesoundofaiosr.github.io/).

The original base model is pretrained and fine-tuned on 960 hours of Librispeech on 16kHz sampled speech audio. When using the model make sure that your speech input is also sampled at 16Khz.

## Paper

Authors: Alexei Baevski, Henry Zhou, Abdelrahman Mohamed, Michael Auli

## Abstract

We show for the first time that learning powerful representations from speech audio alone followed by fine-tuning on transcribed speech can outperform the best semi-supervised methods while being conceptually simpler. wav2vec 2.0 masks the speech input in the latent space and solves a contrastive task defined over a quantization of the latent representations which are jointly learned. Experiments using all labeled data of Librispeech achieve 1.8/3.3 WER on the clean/other test sets. When lowering the amount of labeled data to one hour, wav2vec 2.0 outperforms the previous state of the art on the 100 hour subset while using 100 times less labeled data. Using just ten minutes of labeled data and pre-training on 53k hours of unlabeled data still achieves 4.8/8.2 WER. This demonstrates the feasibility of speech recognition with limited amounts of labeled data.

The original model can be found under https://github.com/pytorch/fairseq/tree/master/examples/wav2vec#wav2vec-20.
The original model can also be found in hugging face public model repository [here](https://huggingface.co/facebook/wav2vec2-base-960h)

## Usage
```python
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset
import soundfile as sf
import torch

# load tokenizer, data_processor and model
tokenizer = Wav2Vec2CTCTokenizer.from_pretrained("iamtarun/wav2vec-osr")
processor = Wav2Vec2Processor.from_pretrained("iamtarun/wav2vec-osr")
model = Wav2Vec2ForCTC.from_pretrained("iamtarun/wav2vec-osr")

model = model.eval()

device = "cuda" if torch.cuda.is_available() else "cpu"
model = model.to(device)

# define function to read in sound file
def map_to_array(batch):
   speech, _ = sf.read(batch["file"])
   batch["speech"] = speech
   return batch

# load dummy dataset and read soundfiles
ds = load_dataset("patrickvonplaten/librispeech_asr_dummy", "clean", split="validation")
ds = ds.map(map_to_array)

# speech data is passed to data processor whose output is then fed to model
input_values = processor(ds["speech"][:2], sampling_rate=rate, padding="longest", return_tensors="pt").input_values.to(device)

# retrieve logits
logits = model(input_values).logits

# take argmax and decode
predicted_ids = torch.argmax(logits, dim =-1)
transcriptions = tokenizer.decode(predicted_ids[0])
print(transcriptions)
 ```