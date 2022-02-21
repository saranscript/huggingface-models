---
language:
- id
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: 'XLS-R-300M - Indonesia'
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 38.098
       - name: Test CER
         type: cer
         value: 14.261
  
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ID dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3975
- Wer: 0.2633

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
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 0.78  | 100  | 4.5645          | 1.0    |
| No log        | 1.55  | 200  | 2.9016          | 1.0    |
| No log        | 2.33  | 300  | 2.2666          | 1.0982 |
| No log        | 3.1   | 400  | 0.6079          | 0.6376 |
| 3.2188        | 3.88  | 500  | 0.4985          | 0.5008 |
| 3.2188        | 4.65  | 600  | 0.4477          | 0.4469 |
| 3.2188        | 5.43  | 700  | 0.3953          | 0.3915 |
| 3.2188        | 6.2   | 800  | 0.4319          | 0.3921 |
| 3.2188        | 6.98  | 900  | 0.4171          | 0.3698 |
| 0.2193        | 7.75  | 1000 | 0.3957          | 0.3600 |
| 0.2193        | 8.53  | 1100 | 0.3730          | 0.3493 |
| 0.2193        | 9.3   | 1200 | 0.3780          | 0.3348 |
| 0.2193        | 10.08 | 1300 | 0.4133          | 0.3568 |
| 0.2193        | 10.85 | 1400 | 0.3984          | 0.3193 |
| 0.1129        | 11.63 | 1500 | 0.3845          | 0.3174 |
| 0.1129        | 12.4  | 1600 | 0.3882          | 0.3162 |
| 0.1129        | 13.18 | 1700 | 0.3982          | 0.3008 |
| 0.1129        | 13.95 | 1800 | 0.3902          | 0.3198 |
| 0.1129        | 14.73 | 1900 | 0.4082          | 0.3237 |
| 0.0765        | 15.5  | 2000 | 0.3732          | 0.3126 |
| 0.0765        | 16.28 | 2100 | 0.3893          | 0.3001 |
| 0.0765        | 17.05 | 2200 | 0.4168          | 0.3083 |
| 0.0765        | 17.83 | 2300 | 0.4193          | 0.3044 |
| 0.0765        | 18.6  | 2400 | 0.4006          | 0.3013 |
| 0.0588        | 19.38 | 2500 | 0.3836          | 0.2892 |
| 0.0588        | 20.16 | 2600 | 0.3761          | 0.2903 |
| 0.0588        | 20.93 | 2700 | 0.3895          | 0.2930 |
| 0.0588        | 21.71 | 2800 | 0.3885          | 0.2791 |
| 0.0588        | 22.48 | 2900 | 0.3902          | 0.2891 |
| 0.0448        | 23.26 | 3000 | 0.4200          | 0.2849 |
| 0.0448        | 24.03 | 3100 | 0.4013          | 0.2799 |
| 0.0448        | 24.81 | 3200 | 0.4039          | 0.2731 |
| 0.0448        | 25.58 | 3300 | 0.3970          | 0.2647 |
| 0.0448        | 26.36 | 3400 | 0.4081          | 0.2690 |
| 0.0351        | 27.13 | 3500 | 0.4090          | 0.2674 |
| 0.0351        | 27.91 | 3600 | 0.3953          | 0.2663 |
| 0.0351        | 28.68 | 3700 | 0.4044          | 0.2650 |
| 0.0351        | 29.46 | 3800 | 0.3969          | 0.2646 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
