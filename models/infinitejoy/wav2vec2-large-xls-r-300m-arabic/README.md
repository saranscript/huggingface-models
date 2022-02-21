---
language:
- ar
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- ar
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Arabic
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: ar
    metrics:
       - name: Test WER
         type: wer
         value: NA
       - name: Test CER
         type: cer
         value: NA
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: ar
    metrics:
       - name: Test WER
         type: wer
         value: NA
       - name: Test CER
         type: cer
         value: NA
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300m-SV

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - AR dataset.
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
- learning_rate: 7.5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results



### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py \
    --model_id infinitejoy/wav2vec2-large-xls-r-300m-arabic \
    --dataset mozilla-foundation/common_voice_7_0 --config ar --split test --log_outputs
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py \
    --model_id infinitejoy/wav2vec2-large-xls-r-300m-arabic --dataset speech-recognition-community-v2/dev_data \
    --config ar --split validation --chunk_length_s 10 --stride_length_s 1
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F


model_id = "infinitejoy/wav2vec2-large-xls-r-300m-arabic"

sample_iter = iter(load_dataset("mozilla-foundation/common_voice_7_0", "ar", split="test", streaming=True, use_auth_token=True))

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

| Without LM | With LM (run `./eval.py`) |
|---|---|
| NA | NA |

