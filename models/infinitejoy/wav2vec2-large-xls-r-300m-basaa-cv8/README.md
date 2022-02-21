---
language:
- bas
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- bas
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Basaa
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: bas
    metrics:
       - name: Test WER
         type: wer
         value: 38.057
       - name: Test CER
         type: cer
         value: 11.233
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-basaa-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - BAS dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4648
- Wer: 0.5472

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9421        | 12.82 | 500  | 2.8894          | 1.0    |
| 1.1872        | 25.64 | 1000 | 0.6688          | 0.7460 |
| 0.8894        | 38.46 | 1500 | 0.4868          | 0.6516 |
| 0.769         | 51.28 | 2000 | 0.4960          | 0.6507 |
| 0.6936        | 64.1  | 2500 | 0.4781          | 0.5384 |
| 0.624         | 76.92 | 3000 | 0.4643          | 0.5430 |
| 0.5966        | 89.74 | 3500 | 0.4530          | 0.5591 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
