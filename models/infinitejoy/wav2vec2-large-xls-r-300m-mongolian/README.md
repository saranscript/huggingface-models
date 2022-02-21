---
language:
- mn
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- mn
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Mongolian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: mn
    metrics:
       - name: Test WER
         type: wer
         value: 44.709
       - name: Test CER
         type: cer
         value: 13.532
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: mn
    metrics:
       - name: Test WER
         type: wer
         value: 76.643
       - name: Test CER
         type: cer
         value: 36.997
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-mongolian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - MN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6003
- Wer: 0.4473

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 32
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.3677        | 15.87 | 2000  | 0.6432          | 0.6198 |
| 1.1379        | 31.75 | 4000  | 0.6196          | 0.5592 |
| 1.0093        | 47.62 | 6000  | 0.5828          | 0.5117 |
| 0.8888        | 63.49 | 8000  | 0.5754          | 0.4822 |
| 0.7985        | 79.37 | 10000 | 0.5987          | 0.4690 |
| 0.697         | 95.24 | 12000 | 0.6014          | 0.4471 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
