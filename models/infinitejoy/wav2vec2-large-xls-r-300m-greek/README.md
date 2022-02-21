---
language:
- el
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- el
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Greek
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: el
    metrics:
       - name: Test WER
         type: wer
         value: 102.23963133640552
       - name: Test CER
         type: cer
         value: 146.28
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: el
    metrics:
       - name: Test WER
         type: wer
         value: 99.92
       - name: Test CER
         type: cer
         value: 132.38
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-greek

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - EL dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6592
- Wer: 0.4564

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
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.0928        | 4.42  | 500   | 3.0804          | 1.0073 |
| 1.4505        | 8.85  | 1000  | 0.9038          | 0.7330 |
| 1.2207        | 13.27 | 1500  | 0.7375          | 0.6045 |
| 1.0695        | 17.7  | 2000  | 0.7119          | 0.5441 |
| 1.0104        | 22.12 | 2500  | 0.6069          | 0.5296 |
| 0.9299        | 26.55 | 3000  | 0.6168          | 0.5206 |
| 0.8588        | 30.97 | 3500  | 0.6382          | 0.5171 |
| 0.7942        | 35.4  | 4000  | 0.6048          | 0.4988 |
| 0.7808        | 39.82 | 4500  | 0.6730          | 0.5084 |
| 0.743         | 44.25 | 5000  | 0.6749          | 0.5012 |
| 0.6652        | 48.67 | 5500  | 0.6491          | 0.4735 |
| 0.6386        | 53.1  | 6000  | 0.6928          | 0.4954 |
| 0.5945        | 57.52 | 6500  | 0.6359          | 0.4798 |
| 0.5561        | 61.95 | 7000  | 0.6409          | 0.4799 |
| 0.5464        | 66.37 | 7500  | 0.6452          | 0.4691 |
| 0.5119        | 70.8  | 8000  | 0.6376          | 0.4657 |
| 0.474         | 75.22 | 8500  | 0.6541          | 0.4700 |
| 0.45          | 79.65 | 9000  | 0.6374          | 0.4571 |
| 0.4315        | 84.07 | 9500  | 0.6568          | 0.4625 |
| 0.3967        | 88.5  | 10000 | 0.6636          | 0.4605 |
| 0.3937        | 92.92 | 10500 | 0.6537          | 0.4597 |
| 0.3788        | 97.35 | 11000 | 0.6614          | 0.4589 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
