---
language:
- pt
license: apache-2.0
tags:
- generated_from_trainer
- pt
- robust-speech-event
datasets:
- common_voice
model-index:
- name: sew-tiny-portuguese-cv
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 6
      type: common_voice
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 30.02
       - name: Test CER
         type: cer
         value: 10.34
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
         value: 56.46
       - name: Test CER
         type: cer
         value: 22.94
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-tiny-portuguese-cv

This model is a fine-tuned version of [lgris/sew-tiny-pt](https://huggingface.co/lgris/sew-tiny-pt) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5110
- Wer: 0.2842

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

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| No log        | 4.92   | 1000  | 0.8468          | 0.6494 |
| 3.4638        | 9.85   | 2000  | 0.4978          | 0.3815 |
| 3.4638        | 14.78  | 3000  | 0.4734          | 0.3417 |
| 0.9904        | 19.7   | 4000  | 0.4577          | 0.3344 |
| 0.9904        | 24.63  | 5000  | 0.4376          | 0.3170 |
| 0.8849        | 29.55  | 6000  | 0.4225          | 0.3118 |
| 0.8849        | 34.48  | 7000  | 0.4354          | 0.3080 |
| 0.819         | 39.41  | 8000  | 0.4434          | 0.3004 |
| 0.819         | 44.33  | 9000  | 0.4710          | 0.3132 |
| 0.7706        | 49.26  | 10000 | 0.4497          | 0.3064 |
| 0.7706        | 54.19  | 11000 | 0.4598          | 0.3100 |
| 0.7264        | 59.11  | 12000 | 0.4271          | 0.3013 |
| 0.7264        | 64.04  | 13000 | 0.4333          | 0.2959 |
| 0.6909        | 68.96  | 14000 | 0.4554          | 0.3019 |
| 0.6909        | 73.89  | 15000 | 0.4444          | 0.2888 |
| 0.6614        | 78.81  | 16000 | 0.4734          | 0.3081 |
| 0.6614        | 83.74  | 17000 | 0.4820          | 0.3058 |
| 0.6379        | 88.67  | 18000 | 0.4416          | 0.2950 |
| 0.6379        | 93.59  | 19000 | 0.4614          | 0.2974 |
| 0.6055        | 98.52  | 20000 | 0.4812          | 0.3018 |
| 0.6055        | 103.45 | 21000 | 0.4700          | 0.3018 |
| 0.5823        | 108.37 | 22000 | 0.4726          | 0.2999 |
| 0.5823        | 113.3  | 23000 | 0.4979          | 0.2887 |
| 0.5597        | 118.23 | 24000 | 0.4813          | 0.2980 |
| 0.5597        | 123.15 | 25000 | 0.4968          | 0.2972 |
| 0.542         | 128.08 | 26000 | 0.5331          | 0.3059 |
| 0.542         | 133.0  | 27000 | 0.5046          | 0.2978 |
| 0.5185        | 137.93 | 28000 | 0.4882          | 0.2922 |
| 0.5185        | 142.85 | 29000 | 0.4945          | 0.2938 |
| 0.499         | 147.78 | 30000 | 0.4971          | 0.2913 |
| 0.499         | 152.71 | 31000 | 0.4948          | 0.2873 |
| 0.4811        | 157.63 | 32000 | 0.4924          | 0.2918 |
| 0.4811        | 162.56 | 33000 | 0.5128          | 0.2911 |
| 0.4679        | 167.49 | 34000 | 0.5098          | 0.2892 |
| 0.4679        | 172.41 | 35000 | 0.4966          | 0.2863 |
| 0.456         | 177.34 | 36000 | 0.5033          | 0.2839 |
| 0.456         | 182.27 | 37000 | 0.5114          | 0.2875 |
| 0.4453        | 187.19 | 38000 | 0.5154          | 0.2859 |
| 0.4453        | 192.12 | 39000 | 0.5102          | 0.2847 |
| 0.4366        | 197.04 | 40000 | 0.5110          | 0.2842 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
