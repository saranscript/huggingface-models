---
language:
- pt
license: apache-2.0
tags:
- generated_from_trainer
- pt
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: sew-tiny-portuguese-cv8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 33.71
       - name: Test CER
         type: cer
         value: 10.69
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: sv
    metrics:
       - name: Test WER
         type: wer
         value: 52.79
       - name: Test CER
         type: cer
         value: 20.98
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-tiny-portuguese-cv8

This model is a fine-tuned version of [lgris/sew-tiny-pt](https://huggingface.co/lgris/sew-tiny-pt) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4082
- Wer: 0.3053

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- training_steps: 40000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| No log        | 1.93  | 1000  | 2.9134          | 0.9767 |
| 2.9224        | 3.86  | 2000  | 2.8405          | 0.9789 |
| 2.9224        | 5.79  | 3000  | 2.8094          | 0.9800 |
| 2.8531        | 7.72  | 4000  | 2.7439          | 0.9891 |
| 2.8531        | 9.65  | 5000  | 2.7057          | 1.0159 |
| 2.7721        | 11.58 | 6000  | 2.7235          | 1.0709 |
| 2.7721        | 13.51 | 7000  | 2.5931          | 1.1035 |
| 2.6566        | 15.44 | 8000  | 2.2171          | 0.9884 |
| 2.6566        | 17.37 | 9000  | 1.2399          | 0.8081 |
| 1.9558        | 19.31 | 10000 | 0.9045          | 0.6353 |
| 1.9558        | 21.24 | 11000 | 0.7705          | 0.5533 |
| 1.4987        | 23.17 | 12000 | 0.7068          | 0.5165 |
| 1.4987        | 25.1  | 13000 | 0.6641          | 0.4718 |
| 1.3811        | 27.03 | 14000 | 0.6043          | 0.4470 |
| 1.3811        | 28.96 | 15000 | 0.5532          | 0.4268 |
| 1.2897        | 30.89 | 16000 | 0.5371          | 0.4101 |
| 1.2897        | 32.82 | 17000 | 0.5924          | 0.4150 |
| 1.225         | 34.75 | 18000 | 0.4949          | 0.3894 |
| 1.225         | 36.68 | 19000 | 0.5591          | 0.4045 |
| 1.193         | 38.61 | 20000 | 0.4927          | 0.3731 |
| 1.193         | 40.54 | 21000 | 0.4922          | 0.3712 |
| 1.1482        | 42.47 | 22000 | 0.4799          | 0.3662 |
| 1.1482        | 44.4  | 23000 | 0.4846          | 0.3648 |
| 1.1201        | 46.33 | 24000 | 0.4770          | 0.3623 |
| 1.1201        | 48.26 | 25000 | 0.4530          | 0.3426 |
| 1.0892        | 50.19 | 26000 | 0.4523          | 0.3527 |
| 1.0892        | 52.12 | 27000 | 0.4573          | 0.3443 |
| 1.0583        | 54.05 | 28000 | 0.4488          | 0.3353 |
| 1.0583        | 55.98 | 29000 | 0.4295          | 0.3285 |
| 1.0319        | 57.92 | 30000 | 0.4321          | 0.3220 |
| 1.0319        | 59.85 | 31000 | 0.4244          | 0.3236 |
| 1.0076        | 61.78 | 32000 | 0.4197          | 0.3201 |
| 1.0076        | 63.71 | 33000 | 0.4230          | 0.3208 |
| 0.9851        | 65.64 | 34000 | 0.4090          | 0.3127 |
| 0.9851        | 67.57 | 35000 | 0.4088          | 0.3133 |
| 0.9695        | 69.5  | 36000 | 0.4123          | 0.3088 |
| 0.9695        | 71.43 | 37000 | 0.4017          | 0.3090 |
| 0.9514        | 73.36 | 38000 | 0.4184          | 0.3086 |
| 0.9514        | 75.29 | 39000 | 0.4075          | 0.3043 |
| 0.944         | 77.22 | 40000 | 0.4082          | 0.3053 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
