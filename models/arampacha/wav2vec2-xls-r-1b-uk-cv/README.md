---
language:
- uk
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-1b-hy-cv
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice uk
      args: uk
    metrics:
      - type: wer
        value: 12.246920571994903
        name: WER LM
      - type: cer
        value: 2.513653497966816
        name: CER LM
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - UK dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1747
- Wer: 0.2107
- Cer: 0.0408

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 8e-05
- train_batch_size: 16
- eval_batch_size: 64
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.1
- training_steps: 8000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 1.3719        | 4.35  | 500  | 0.3389          | 0.4236 | 0.0833 |
| 1.1361        | 8.7   | 1000 | 0.2309          | 0.3162 | 0.0630 |
| 1.0517        | 13.04 | 1500 | 0.2166          | 0.3056 | 0.0597 |
| 1.0118        | 17.39 | 2000 | 0.2141          | 0.2784 | 0.0557 |
| 0.9922        | 21.74 | 2500 | 0.2231          | 0.2941 | 0.0594 |
| 0.9929        | 26.09 | 3000 | 0.2171          | 0.2892 | 0.0587 |
| 0.9485        | 30.43 | 3500 | 0.2236          | 0.2956 | 0.0599 |
| 0.9573        | 34.78 | 4000 | 0.2314          | 0.3043 | 0.0616 |
| 0.9195        | 39.13 | 4500 | 0.2169          | 0.2812 | 0.0580 |
| 0.8915        | 43.48 | 5000 | 0.2109          | 0.2780 | 0.0560 |
| 0.8449        | 47.83 | 5500 | 0.2050          | 0.2534 | 0.0514 |
| 0.8028        | 52.17 | 6000 | 0.2032          | 0.2456 | 0.0492 |
| 0.7881        | 56.52 | 6500 | 0.1890          | 0.2380 | 0.0469 |
| 0.7423        | 60.87 | 7000 | 0.1816          | 0.2245 | 0.0442 |
| 0.7248        | 65.22 | 7500 | 0.1789          | 0.2165 | 0.0422 |
| 0.6993        | 69.57 | 8000 | 0.1747          | 0.2107 | 0.0408 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
