---
language:
- br
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- br
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Breton
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: br
    metrics:
       - name: Test WER
         type: wer
         value: 54.855
       - name: Test CER
         type: cer
         value: 17.865
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M - Breton

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - BR dataset.
It achieves the following results on the evaluation set:
- Loss: NA
- Wer: NA

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:

### Training results

NA

### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id infinitejoy/wav2vec2-large-xls-r-300m-breton-cv8 --dataset mozilla-foundation/common_voice_8_0 --config br --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id infinitejoy/wav2vec2-large-xls-r-300m-breton-cv8 --dataset speech-recognition-community-v2/dev_data --config br --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F


model_id = "infinitejoy/wav2vec2-large-xls-r-300m-breton-cv8"

sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "br", split="test", streaming=True, use_auth_token=True))

sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()

model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)

input_values = processor(resampled_audio, return_tensors="pt").input_values

with torch.no_grad():
    logits = model(input_values).logits

transcription = processor.batch_decode(logits.numpy()).text

```

### Eval results on Common Voice 7 "test" (WER):

NA

