---
language:
- et
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
- et
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: 'xls-r-et-cv_8_0'
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: et
    metrics:
       - name: Test WER
         type: wer
         value: 0.34180826781638346
       - name: Test CER
         type: cer
         value: 0.07356192733576256 
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ET dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4623
- Wer: 0.3420

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
- train_batch_size: 72
- eval_batch_size: 72
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 144
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.3082        | 12.5  | 500  | 0.3871          | 0.4907 |
| 0.1497        | 25.0  | 1000 | 0.4168          | 0.4278 |
| 0.1243        | 37.5  | 1500 | 0.4446          | 0.4220 |
| 0.0954        | 50.0  | 2000 | 0.4426          | 0.3946 |
| 0.0741        | 62.5  | 2500 | 0.4502          | 0.3800 |
| 0.0533        | 75.0  | 3000 | 0.4618          | 0.3653 |
| 0.0447        | 87.5  | 3500 | 0.4518          | 0.3461 |
| 0.0396        | 100.0 | 4000 | 0.4623          | 0.3420 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
