---
language:
- lv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- lv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Latvian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: lv
    metrics:
       - name: Test WER
         type: wer
         value: 16.977
       - name: Test CER
         type: cer
         value: 4.230
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: lv
    metrics:
       - name: Test WER
         type: wer
         value: 45.247
       - name: Test CER
         type: cer
         value: 16.924
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-latvian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - LV dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1892
- Wer: 0.1698

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
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.4235        | 12.82 | 2000  | 0.4475          | 0.4551 |
| 0.9383        | 25.64 | 4000  | 0.2235          | 0.2328 |
| 0.8359        | 38.46 | 6000  | 0.2004          | 0.2098 |
| 0.7633        | 51.28 | 8000  | 0.1960          | 0.1882 |
| 0.7001        | 64.1  | 10000 | 0.1902          | 0.1809 |
| 0.652         | 76.92 | 12000 | 0.1979          | 0.1775 |
| 0.6025        | 89.74 | 14000 | 0.1866          | 0.1696 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
