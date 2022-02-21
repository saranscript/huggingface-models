---
language:
- eu
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
- name: 'xls-r-eus'
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: eu
    metrics:
       - name: Test WER
         type: wer
         value: 0.17871523648578164
       - name: Test CER
         type: cer
         value: 0.032624506085144 
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - EU dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2278
- Wer: 0.1787

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

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.2548        | 4.24  | 500   | 0.2470          | 0.3663 |
| 0.1435        | 8.47  | 1000  | 0.2000          | 0.2791 |
| 0.1158        | 12.71 | 1500  | 0.2030          | 0.2652 |
| 0.1094        | 16.95 | 2000  | 0.2096          | 0.2605 |
| 0.1004        | 21.19 | 2500  | 0.2150          | 0.2477 |
| 0.0945        | 25.42 | 3000  | 0.2072          | 0.2369 |
| 0.0844        | 29.66 | 3500  | 0.1981          | 0.2328 |
| 0.0877        | 33.89 | 4000  | 0.2041          | 0.2425 |
| 0.0741        | 38.14 | 4500  | 0.2353          | 0.2421 |
| 0.0676        | 42.37 | 5000  | 0.2092          | 0.2213 |
| 0.0623        | 46.61 | 5500  | 0.2217          | 0.2250 |
| 0.0574        | 50.84 | 6000  | 0.2152          | 0.2179 |
| 0.0583        | 55.08 | 6500  | 0.2207          | 0.2186 |
| 0.0488        | 59.32 | 7000  | 0.2225          | 0.2159 |
| 0.0456        | 63.56 | 7500  | 0.2293          | 0.2031 |
| 0.041         | 67.79 | 8000  | 0.2277          | 0.2013 |
| 0.0379        | 72.03 | 8500  | 0.2287          | 0.1991 |
| 0.0381        | 76.27 | 9000  | 0.2233          | 0.1954 |
| 0.0308        | 80.51 | 9500  | 0.2195          | 0.1835 |
| 0.0291        | 84.74 | 10000 | 0.2266          | 0.1825 |
| 0.0266        | 88.98 | 10500 | 0.2285          | 0.1801 |
| 0.0266        | 93.22 | 11000 | 0.2292          | 0.1801 |
| 0.0262        | 97.46 | 11500 | 0.2278          | 0.1788 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
