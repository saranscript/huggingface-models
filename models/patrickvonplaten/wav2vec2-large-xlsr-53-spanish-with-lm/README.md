---
language: es
datasets:
- common_voice
metrics:
- wer
- cer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
---

# Wav2Vec2-Large-XLSR-53-Spanish-With-LM

This is a model copy of [Wav2Vec2-Large-XLSR-53-Spanish](https://huggingface.co/jonatasgrosman/wav2vec2-large-xlsr-53-spanish)
that has language model support. 

This model card can be seen as a demo for the [pyctcdecode](https://github.com/kensho-technologies/pyctcdecode) integration 
with Transformers led by [this PR](https://github.com/huggingface/transformers/pull/14339). The PR explains in-detail how the 
integration works. 

In a nutshell: This PR adds a new Wav2Vec2WithLMProcessor class as drop-in replacement for Wav2Vec2Processor.

The only change from the existing ASR pipeline will be:

## Changes

```diff
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F


model_id = "patrickvonplaten/wav2vec2-large-xlsr-53-spanish-with-lm"

sample = next(iter(load_dataset("common_voice", "es", split="test", streaming=True)))
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()

model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)

input_values = processor(resampled_audio, return_tensors="pt").input_values

with torch.no_grad():
    logits = model(input_values).logits

-prediction_ids = torch.argmax(logits, dim=-1)
-transcription = processor.batch_decode(prediction_ids)
+transcription = processor.batch_decode(logits.numpy()).text
# => 'bien y qué regalo vas a abrir primero'
```

**Improvement**

This model has been compared on 512 speech samples from the Spanish Common Voice Test set and 
gives a nice *20 %* performance boost:

The results can be reproduced by running *from this model repository*:

| Model | WER | CER |
| ------------- | ------------- | ------------- |
| patrickvonplaten/wav2vec2-large-xlsr-53-spanish-with-lm | **8.44%** | **2.93%** |
| jonatasgrosman/wav2vec2-large-xlsr-53-spanish | **10.20%** | **3.24%** |

```
bash run_ngram_wav2vec2.py 1 512
```

```
bash run_ngram_wav2vec2.py 0 512
```

with `run_ngram_wav2vec2.py` being 
https://huggingface.co/patrickvonplaten/wav2vec2-large-xlsr-53-spanish-with-lm/blob/main/run_ngram_wav2vec2.py