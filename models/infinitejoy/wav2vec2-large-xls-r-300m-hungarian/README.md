---
language:
- hu
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- hu
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Hungarian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: hu
    metrics:
       - name: Test WER
         type: wer
         value: 31.099
       - name: Test CER
         type: cer
         value: 6.737
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: hu
    metrics:
       - name: Test WER
         type: wer
         value: 45.469
       - name: Test CER
         type: cer
         value: 15.727
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-hungarian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HU dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2562
- Wer: 0.3112

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
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.3964        | 3.52  | 1000  | 1.2251          | 0.8781 |
| 1.3176        | 7.04  | 2000  | 0.3872          | 0.4462 |
| 1.1999        | 10.56 | 3000  | 0.3244          | 0.3922 |
| 1.1633        | 14.08 | 4000  | 0.3014          | 0.3704 |
| 1.1132        | 17.61 | 5000  | 0.2913          | 0.3623 |
| 1.0888        | 21.13 | 6000  | 0.2864          | 0.3498 |
| 1.0487        | 24.65 | 7000  | 0.2821          | 0.3435 |
| 1.0431        | 28.17 | 8000  | 0.2739          | 0.3308 |
| 0.9896        | 31.69 | 9000  | 0.2629          | 0.3243 |
| 0.9839        | 35.21 | 10000 | 0.2806          | 0.3308 |
| 0.9586        | 38.73 | 11000 | 0.2650          | 0.3235 |
| 0.9501        | 42.25 | 12000 | 0.2585          | 0.3173 |
| 0.938         | 45.77 | 13000 | 0.2561          | 0.3117 |
| 0.921         | 49.3  | 14000 | 0.2559          | 0.3115 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
