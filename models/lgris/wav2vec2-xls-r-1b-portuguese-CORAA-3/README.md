---
language:
- pt
license: apache-2.0
tags:
- automatic-speech-recognition
- generated_from_trainer
- pt
- robust-speech-event
model-index:
- name: wav2vec2-xls-r-1b-portuguese-CORAA-3
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
         value: 71.67
       - name: Test CER
         type: cer
         value: 30.64
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
         value: 68.18
       - name: Test CER
         type: cer
         value: 28.34
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
         value: 56.76
       - name: Test CER
         type: cer
         value: 23.70
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-1b-portuguese-CORAA-3

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on [CORAA dataset](https://github.com/nilc-nlp/CORAA).
It achieves the following results on the evaluation set:
- Loss: 1.0029
- Wer: 0.6020

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 5000
- training_steps: 30000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.0169        | 0.21  | 5000  | 1.9582          | 0.9283 |
| 1.8561        | 0.42  | 10000 | 1.6144          | 0.8554 |
| 1.6823        | 0.63  | 15000 | 1.4165          | 0.7710 |
| 1.52          | 0.84  | 20000 | 1.2441          | 0.7289 |
| 1.3757        | 1.05  | 25000 | 1.1061          | 0.6491 |
| 1.2377        | 1.26  | 30000 | 1.0029          | 0.6020 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3.dev0
- Tokenizers 0.11.0
