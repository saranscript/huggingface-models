---
language:
- bg
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Bulgarian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: bg
    metrics:
       - name: Test WER
         type: wer
         value: 21.195
       - name: Test CER
         type: cer
         value: 4.786
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: bg
    metrics:
       - name: Test WER
         type: wer
         value: 32.667
       - name: Test CER
         type: cer
         value: 12.452
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M - Bulgarian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - BG dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2473
- Wer: 0.3002

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
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.1589        | 3.48  | 400  | 3.0830          | 1.0    |
| 2.8921        | 6.96  | 800  | 2.6605          | 0.9982 |
| 1.3049        | 10.43 | 1200 | 0.5069          | 0.5707 |
| 1.1349        | 13.91 | 1600 | 0.4159          | 0.5041 |
| 1.0686        | 17.39 | 2000 | 0.3815          | 0.4746 |
| 0.999         | 20.87 | 2400 | 0.3541          | 0.4343 |
| 0.945         | 24.35 | 2800 | 0.3266          | 0.4132 |
| 0.9058        | 27.83 | 3200 | 0.2969          | 0.3771 |
| 0.8672        | 31.3  | 3600 | 0.2802          | 0.3553 |
| 0.8313        | 34.78 | 4000 | 0.2662          | 0.3380 |
| 0.8068        | 38.26 | 4400 | 0.2528          | 0.3181 |
| 0.7796        | 41.74 | 4800 | 0.2537          | 0.3073 |
| 0.7621        | 45.22 | 5200 | 0.2503          | 0.3036 |
| 0.7611        | 48.7  | 5600 | 0.2477          | 0.2991 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0


#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-large-xls-r-300m-bg --dataset mozilla-foundation/common_voice_8_0 --config bg --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id anuragshas/wav2vec2-large-xls-r-300m-bg --dataset speech-recognition-community-v2/dev_data --config bg --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-large-xls-r-300m-bg"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "bg", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "и надутият му ката блоонкурем взе да се събира"
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 30.07 | 21.195 |
