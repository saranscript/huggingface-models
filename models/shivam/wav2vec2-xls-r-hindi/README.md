---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- hi
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
metrics:
- wer
- cer
model-index:
- name: 'shivam/wav2vec2-xls-r-hindi'
  results:
  - task:
      type: automatic-speech-recognition
      name: Automatic Speech Recognition 
    dataset:
      name: Common Voice Corpus 7.0
      type: mozilla-foundation/common_voice_7_0
      args: hi
    metrics:
       - name: Test WER
         type: wer
         value: 52.30
       - name: Test CER
         type: cer
         value: 26.09
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2282
- Wer: 0.6838

## Evaluation results on Common Voice 7 "test" (Running ./eval.py):

### With LM
- WER: 52.30
- CER: 26.09

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

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.3155        | 3.4   | 500  | 4.5582          | 1.0    |
| 3.3369        | 6.8   | 1000 | 3.4269          | 1.0    |
| 2.1785        | 10.2  | 1500 | 1.7191          | 0.8831 |
| 1.579         | 13.6  | 2000 | 1.3604          | 0.7647 |
| 1.3773        | 17.01 | 2500 | 1.2737          | 0.7519 |
| 1.3165        | 20.41 | 3000 | 1.2457          | 0.7401 |
| 1.2274        | 23.81 | 3500 | 1.3617          | 0.7301 |
| 1.1787        | 27.21 | 4000 | 1.2068          | 0.7010 |
| 1.1467        | 30.61 | 4500 | 1.2416          | 0.6946 |
| 1.0801        | 34.01 | 5000 | 1.2312          | 0.6990 |
| 1.0709        | 37.41 | 5500 | 1.2984          | 0.7138 |
| 1.0307        | 40.81 | 6000 | 1.2049          | 0.6871 |
| 1.0003        | 44.22 | 6500 | 1.1956          | 0.6841 |
| 1.004         | 47.62 | 7000 | 1.2101          | 0.6793 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu113
- Datasets 1.18.1.dev0
- Tokenizers 0.11.0
