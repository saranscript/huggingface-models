---
language:
- ga-IE
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- ga-IE
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: wav2vec-cv7-1b-ir
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: ga-IE
    metrics:
       - name: Test WER
         type: wer
         value: 39.1
       - name: Test CER
         type: cer
         value: 16.4
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - GA-IE dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9562
- Wer: 0.4801

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.3731        | 15.62 | 500  | 1.5517          | 0.9499 |
| 1.3312        | 31.25 | 1000 | 0.8717          | 0.6189 |
| 0.9135        | 46.86 | 1500 | 0.8299          | 0.5310 |
| 0.6719        | 62.49 | 2000 | 0.8842          | 0.5044 |
| 0.5583        | 78.12 | 2500 | 0.9093          | 0.4801 |
| 0.4728        | 93.74 | 3000 | 0.9488          | 0.4813 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
