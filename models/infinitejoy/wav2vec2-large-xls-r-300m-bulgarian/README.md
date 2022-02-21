---
language:
- bg
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- bg
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Bulgarian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: bg
    metrics:
       - name: Test WER
         type: wer
         value: 46.68
       - name: Test CER
         type: cer
         value: 10.75
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
         value: 63.68
       - name: Test CER
         type: cer
         value: 19.88
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-bulgarian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - BG dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4487
- Wer: 0.4674

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9774        | 6.33  | 500  | 2.9769          | 1.0    |
| 1.3453        | 12.66 | 1000 | 0.6523          | 0.6980 |
| 1.1658        | 18.99 | 1500 | 0.5636          | 0.6359 |
| 1.0797        | 25.32 | 2000 | 0.5004          | 0.5759 |
| 1.044         | 31.65 | 2500 | 0.4958          | 0.5569 |
| 0.9915        | 37.97 | 3000 | 0.4971          | 0.5350 |
| 0.9429        | 44.3  | 3500 | 0.4829          | 0.5229 |
| 0.9266        | 50.63 | 4000 | 0.4515          | 0.5074 |
| 0.8965        | 56.96 | 4500 | 0.4599          | 0.5039 |
| 0.878         | 63.29 | 5000 | 0.4735          | 0.4954 |
| 0.8494        | 69.62 | 5500 | 0.4460          | 0.4878 |
| 0.8343        | 75.95 | 6000 | 0.4510          | 0.4795 |
| 0.8236        | 82.28 | 6500 | 0.4538          | 0.4789 |
| 0.8069        | 88.61 | 7000 | 0.4526          | 0.4748 |
| 0.7958        | 94.94 | 7500 | 0.4496          | 0.4700 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
