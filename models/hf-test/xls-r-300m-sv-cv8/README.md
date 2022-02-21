---
language:
- sv-SE
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Swedish - CV8
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
         value: 17.10
       - name: Test CER
         type: cer
         value: 5.70
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
         value: 26.92
       - name: Test CER
         type: cer
         value: 12.53
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SV-SE dataset.
It achieves the following results on the evaluation set:

**Without LM**:

- Wer: 0.2465
- Cer: 0.0717

**With LM**:

- Wer: 0.1710
- Cer: 0.0569

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

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.3224        | 1.37  | 500   | 3.2676          | 1.0    |
| 2.9319        | 2.74  | 1000  | 2.9287          | 1.0000 |
| 2.1173        | 4.11  | 1500  | 1.1478          | 0.8788 |
| 1.6973        | 5.48  | 2000  | 0.6749          | 0.6547 |
| 1.5865        | 6.85  | 2500  | 0.5500          | 0.5634 |
| 1.5094        | 8.22  | 3000  | 0.4840          | 0.5430 |
| 1.4644        | 9.59  | 3500  | 0.4844          | 0.4142 |
| 1.4061        | 10.96 | 4000  | 0.4356          | 0.3808 |
| 1.3584        | 12.33 | 4500  | 0.4192          | 0.3698 |
| 1.3438        | 13.7  | 5000  | 0.3980          | 0.3584 |
| 1.3332        | 15.07 | 5500  | 0.3896          | 0.3572 |
| 1.3025        | 16.44 | 6000  | 0.3835          | 0.3487 |
| 1.2979        | 17.81 | 6500  | 0.3781          | 0.3417 |
| 1.2736        | 19.18 | 7000  | 0.3734          | 0.3270 |
| 1.2415        | 20.55 | 7500  | 0.3637          | 0.3316 |
| 1.2255        | 21.92 | 8000  | 0.3546          | 0.3147 |
| 1.2193        | 23.29 | 8500  | 0.3524          | 0.3196 |
| 1.2104        | 24.66 | 9000  | 0.3403          | 0.3097 |
| 1.1965        | 26.03 | 9500  | 0.3508          | 0.3093 |
| 1.1976        | 27.4  | 10000 | 0.3419          | 0.3071 |
| 1.182         | 28.77 | 10500 | 0.3364          | 0.2963 |
| 1.158         | 30.14 | 11000 | 0.3338          | 0.2932 |
| 1.1414        | 31.51 | 11500 | 0.3376          | 0.2940 |
| 1.1402        | 32.88 | 12000 | 0.3370          | 0.2891 |
| 1.1213        | 34.25 | 12500 | 0.3201          | 0.2874 |
| 1.1207        | 35.62 | 13000 | 0.3261          | 0.2826 |
| 1.1074        | 36.98 | 13500 | 0.3117          | 0.2786 |
| 1.0818        | 38.36 | 14000 | 0.3194          | 0.2776 |
| 1.0889        | 39.73 | 14500 | 0.3188          | 0.2738 |
| 1.0672        | 41.1  | 15000 | 0.3196          | 0.2773 |
| 1.0838        | 42.47 | 15500 | 0.3130          | 0.2739 |
| 1.0553        | 43.83 | 16000 | 0.3165          | 0.2704 |
| 1.0786        | 45.21 | 16500 | 0.3108          | 0.2706 |
| 1.0546        | 46.57 | 17000 | 0.3102          | 0.2677 |
| 1.0425        | 47.94 | 17500 | 0.3115          | 0.2679 |
| 1.0398        | 49.31 | 18000 | 0.3131          | 0.2666 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu113
- Datasets 1.18.1.dev0
- Tokenizers 0.10.3
