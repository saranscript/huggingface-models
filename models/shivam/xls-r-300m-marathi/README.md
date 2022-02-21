---
language:
- mr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- mr
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: ''
  results:
  - task: 
      type: automatic-speech-recognition
      name: Automatic Speech Recognition 
    dataset:
      name: Common Voice Corpus 8.0
      type: mozilla-foundation/common_voice_8_0
      args: mr
    metrics:
       - name: Test WER
         type: wer
         value: 38.27
       - name: Test CER
         type: cer
         value: 8.91
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - MR dataset.
It achieves the following results on the mozilla-foundation/common_voice_8_0 mr test set:

- Without LM
  + WER: 48.53
  + CER: 10.63
   
- With LM
  + WER: 38.27
  + CER: 8.91

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
- num_epochs: 400.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 4.2706        | 22.73  | 500  | 4.0174          | 1.0    |
| 3.2492        | 45.45  | 1000 | 3.2309          | 0.9908 |
| 1.9709        | 68.18  | 1500 | 1.0651          | 0.8440 |
| 1.4088        | 90.91  | 2000 | 0.5765          | 0.6550 |
| 1.1326        | 113.64 | 2500 | 0.4842          | 0.5760 |
| 0.9709        | 136.36 | 3000 | 0.4785          | 0.6013 |
| 0.8433        | 159.09 | 3500 | 0.5048          | 0.5419 |
| 0.7404        | 181.82 | 4000 | 0.5052          | 0.5339 |
| 0.6589        | 204.55 | 4500 | 0.5237          | 0.5897 |
| 0.5831        | 227.27 | 5000 | 0.5166          | 0.5447 |
| 0.5375        | 250.0  | 5500 | 0.5292          | 0.5487 |
| 0.4784        | 272.73 | 6000 | 0.5480          | 0.5596 |
| 0.4421        | 295.45 | 6500 | 0.5682          | 0.5467 |
| 0.4047        | 318.18 | 7000 | 0.5681          | 0.5447 |
| 0.3779        | 340.91 | 7500 | 0.5783          | 0.5347 |
| 0.3525        | 363.64 | 8000 | 0.5856          | 0.5367 |
| 0.3393        | 386.36 | 8500 | 0.5960          | 0.5359 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu113
- Datasets 1.18.1.dev0
- Tokenizers 0.11.0
