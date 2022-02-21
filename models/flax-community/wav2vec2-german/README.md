---
language: de
datasets:
- librispeech_asr
tags:
- speech
license: apache-2.0
---

# Wav2Vec2-german model

[Facebook's Wav2Vec2](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio/)

The base model pretrained on 16kHz sampled speech audio. When using the model make sure that your speech input is also sampled at 16Khz. Note that this model should be fine-tuned on a downstream task, like Automatic Speech Recognition. Check out [this blog](https://huggingface.co/blog/fine-tune-wav2vec2-english) for more information.

[Paper](https://arxiv.org/abs/2006.11477)

Authors: Alexei Baevski, Henry Zhou, Abdelrahman Mohamed, Michael Auli

**Abstract**
We show for the first time that learning powerful representations from speech audio alone followed by fine-tuning on transcribed speech can outperform the best semi-supervised methods while being conceptually simpler. wav2vec 2.0 masks the speech input in the latent space and solves a contrastive task defined over a quantization of the latent representations which are jointly learned. Experiments using all labeled data of Librispeech achieve 1.8/3.3 WER on the clean/other test sets. When lowering the amount of labeled data to one hour, wav2vec 2.0 outperforms the previous state of the art on the 100 hour subset while using 100 times less labeled data. Using just ten minutes of labeled data and pre-training on 53k hours of unlabeled data still achieves 4.8/8.2 WER. This demonstrates the feasibility of speech recognition with limited amounts of labeled data.
The original model can be found under https://github.com/pytorch/fairseq/tree/master/examples/wav2vec#wav2vec-20.

## Necessary installations:

- sndfile library: `sudo apt-get install libsndfile1-dev`
- ffmpeg: `sudo apt install ffmpeg` & `pip install ffmpeg`

## Model description `TODO: Update`

## How to use `TODO: Update`

```python
from transformers import FlaxWav2Vec2Processor, TFWav2Vec2Model

model_id = "flax-community/wav2vec2-german"

from datasets import load_dataset
import soundfile as sf

processor = Wav2Vec2Processor.from_pretrained(model_id)
model = TFWav2Vec2Model.from_pretrained(model_id)

def map_to_array(batch):
    speech, _ = sf.read(batch["file"])
    batch["speech"] = speech
    return batch

ds = load_dataset("patrickvonplaten/librispeech_asr_dummy", "clean", split="validation")
ds = ds.map(map_to_array)

input_values = processor(ds["speech"][0], return_tensors="flax").input_values  # Batch size 1
hidden_states = model(input_values).last_hidden_state
```

## Training Data `TODO: Update`

## Training Procedure `TODO: Update`
