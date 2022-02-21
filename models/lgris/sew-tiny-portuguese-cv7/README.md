---
language:
- pt
license: apache-2.0
tags:
- generated_from_trainer
- pt
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: sew-tiny-portuguese-cv7
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 28.90
       - name: Test CER
         type: cer
         value: 09.41
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
         value: 47.27
       - name: Test CER
         type: cer
         value: 19.62
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-tiny-portuguese-cv7

This model is a fine-tuned version of [lgris/sew-tiny-pt](https://huggingface.co/lgris/sew-tiny-pt) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4232
- Wer: 0.2745

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- training_steps: 40000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| No log        | 2.6    | 1000  | 1.0034          | 0.7308 |
| 4.1307        | 5.19   | 2000  | 0.6274          | 0.4721 |
| 4.1307        | 7.79   | 3000  | 0.5541          | 0.4130 |
| 1.3117        | 10.39  | 4000  | 0.5302          | 0.3880 |
| 1.3117        | 12.99  | 5000  | 0.5082          | 0.3644 |
| 1.2047        | 15.58  | 6000  | 0.4818          | 0.3539 |
| 1.2047        | 18.18  | 7000  | 0.4822          | 0.3477 |
| 1.14          | 20.78  | 8000  | 0.4781          | 0.3428 |
| 1.14          | 23.38  | 9000  | 0.4840          | 0.3401 |
| 1.0818        | 25.97  | 10000 | 0.4613          | 0.3251 |
| 1.0818        | 28.57  | 11000 | 0.4569          | 0.3257 |
| 1.0451        | 31.17  | 12000 | 0.4494          | 0.3132 |
| 1.0451        | 33.77  | 13000 | 0.4560          | 0.3201 |
| 1.011         | 36.36  | 14000 | 0.4687          | 0.3174 |
| 1.011         | 38.96  | 15000 | 0.4397          | 0.3122 |
| 0.9785        | 41.56  | 16000 | 0.4605          | 0.3173 |
| 0.9785        | 44.16  | 17000 | 0.4380          | 0.3064 |
| 0.9458        | 46.75  | 18000 | 0.4372          | 0.3048 |
| 0.9458        | 49.35  | 19000 | 0.4426          | 0.3039 |
| 0.9126        | 51.95  | 20000 | 0.4317          | 0.2962 |
| 0.9126        | 54.54  | 21000 | 0.4345          | 0.2960 |
| 0.8926        | 57.14  | 22000 | 0.4365          | 0.2948 |
| 0.8926        | 59.74  | 23000 | 0.4306          | 0.2940 |
| 0.8654        | 62.34  | 24000 | 0.4303          | 0.2928 |
| 0.8654        | 64.93  | 25000 | 0.4351          | 0.2915 |
| 0.8373        | 67.53  | 26000 | 0.4340          | 0.2909 |
| 0.8373        | 70.13  | 27000 | 0.4279          | 0.2907 |
| 0.83          | 72.73  | 28000 | 0.4214          | 0.2867 |
| 0.83          | 75.32  | 29000 | 0.4256          | 0.2849 |
| 0.8062        | 77.92  | 30000 | 0.4281          | 0.2826 |
| 0.8062        | 80.52  | 31000 | 0.4398          | 0.2865 |
| 0.7846        | 83.12  | 32000 | 0.4218          | 0.2812 |
| 0.7846        | 85.71  | 33000 | 0.4227          | 0.2791 |
| 0.7697        | 88.31  | 34000 | 0.4200          | 0.2767 |
| 0.7697        | 90.91  | 35000 | 0.4285          | 0.2791 |
| 0.7539        | 93.51  | 36000 | 0.4238          | 0.2777 |
| 0.7539        | 96.1   | 37000 | 0.4288          | 0.2757 |
| 0.7413        | 98.7   | 38000 | 0.4205          | 0.2748 |
| 0.7413        | 101.3  | 39000 | 0.4241          | 0.2761 |
| 0.7348        | 103.89 | 40000 | 0.4232          | 0.2745 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
