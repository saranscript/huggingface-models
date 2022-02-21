---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
metrics:
- wer
model-index:
- name: wav2vec2-xls-r-1b-hi-cv7
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_7_0
      name: Common Voice 7
      args: hi
    metrics:
      - type: wer    # Required. Example: wer
        value: 18.504  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - name: Test CER
        type: cer
        value: 6.655
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-1b-hi-cv7

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5878
- Wer: 0.3419

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
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.9859        | 2.72  | 400   | 1.1663          | 0.7948 |
| 1.2969        | 5.44  | 800   | 0.7725          | 0.6562 |
| 1.1954        | 8.16  | 1200  | 0.5940          | 0.4904 |
| 1.164         | 10.88 | 1600  | 0.5338          | 0.4316 |
| 1.1464        | 13.6  | 2000  | 0.5432          | 0.4226 |
| 1.1553        | 16.33 | 2400  | 0.5471          | 0.4260 |
| 1.0985        | 19.05 | 2800  | 0.5290          | 0.4076 |
| 1.0421        | 21.77 | 3200  | 0.5672          | 0.4181 |
| 0.9831        | 24.49 | 3600  | 0.5741          | 0.4141 |
| 0.9827        | 27.21 | 4000  | 0.5754          | 0.4179 |
| 0.9669        | 29.93 | 4400  | 0.5310          | 0.3889 |
| 0.9496        | 32.65 | 4800  | 0.5649          | 0.4062 |
| 0.9112        | 35.37 | 5200  | 0.5738          | 0.3926 |
| 0.8838        | 38.1  | 5600  | 0.5232          | 0.3768 |
| 0.8666        | 40.81 | 6000  | 0.5510          | 0.3852 |
| 0.8366        | 43.54 | 6400  | 0.5436          | 0.3837 |
| 0.7957        | 46.26 | 6800  | 0.5337          | 0.3775 |
| 0.7834        | 48.98 | 7200  | 0.5611          | 0.3844 |
| 0.7685        | 51.7  | 7600  | 0.5710          | 0.4008 |
| 0.7431        | 54.42 | 8000  | 0.5636          | 0.3726 |
| 0.7353        | 57.14 | 8400  | 0.5937          | 0.3836 |
| 0.7001        | 59.86 | 8800  | 0.5815          | 0.3858 |
| 0.6799        | 62.58 | 9200  | 0.5862          | 0.3696 |
| 0.6459        | 65.31 | 9600  | 0.6181          | 0.3762 |
| 0.6121        | 68.03 | 10000 | 0.5637          | 0.3590 |
| 0.5942        | 70.75 | 10400 | 0.6374          | 0.3882 |
| 0.5769        | 73.47 | 10800 | 0.6015          | 0.3640 |
| 0.5689        | 76.19 | 11200 | 0.5669          | 0.3508 |
| 0.5461        | 78.91 | 11600 | 0.5967          | 0.3621 |
| 0.5286        | 81.63 | 12000 | 0.5840          | 0.3605 |
| 0.5057        | 84.35 | 12400 | 0.5848          | 0.3489 |
| 0.482         | 87.07 | 12800 | 0.5860          | 0.3488 |
| 0.4655        | 89.79 | 13200 | 0.5780          | 0.3453 |
| 0.4523        | 92.52 | 13600 | 0.6150          | 0.3532 |
| 0.4422        | 95.24 | 14000 | 0.5930          | 0.3452 |
| 0.4436        | 97.96 | 14400 | 0.5867          | 0.3428 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0


#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-1b-hi --dataset mozilla-foundation/common_voice_7_0 --config hi --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-xls-r-1b-hi"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_7_0", "hi", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "तुम्हारे पास तीन महीने बचे हैं"
```

### Eval results on Common Voice 7 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 28.942 | 18.504 |