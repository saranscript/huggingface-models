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
- common_voice
model-index:
- name: wav2vec2-xls-r-1b-hy
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
        value: 10.406342913776016
        name: WER LM
      - type: cer
        value: 2.0387492208601702
        name: CER LM
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the /WORKSPACE/DATA/UK/COMPOSED_DATASET/ - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1092
- Wer: 0.1752
- Cer: 0.0323

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 64
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.1
- training_steps: 12000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 1.7005        | 1.61  | 500   | 0.4082          | 0.5584 | 0.1164 |
| 1.1555        | 3.22  | 1000  | 0.2020          | 0.2953 | 0.0557 |
| 1.0927        | 4.82  | 1500  | 0.1708          | 0.2584 | 0.0480 |
| 1.0707        | 6.43  | 2000  | 0.1563          | 0.2405 | 0.0450 |
| 1.0728        | 8.04  | 2500  | 0.1620          | 0.2442 | 0.0463 |
| 1.0268        | 9.65  | 3000  | 0.1588          | 0.2378 | 0.0458 |
| 1.0328        | 11.25 | 3500  | 0.1466          | 0.2352 | 0.0442 |
| 1.0249        | 12.86 | 4000  | 0.1552          | 0.2341 | 0.0449 |
| 1.016         | 14.47 | 4500  | 0.1602          | 0.2435 | 0.0473 |
| 1.0164        | 16.08 | 5000  | 0.1491          | 0.2337 | 0.0444 |
| 0.9935        | 17.68 | 5500  | 0.1539          | 0.2373 | 0.0458 |
| 0.9626        | 19.29 | 6000  | 0.1458          | 0.2305 | 0.0434 |
| 0.9505        | 20.9  | 6500  | 0.1368          | 0.2157 | 0.0407 |
| 0.9389        | 22.51 | 7000  | 0.1437          | 0.2231 | 0.0426 |
| 0.9129        | 24.12 | 7500  | 0.1313          | 0.2076 | 0.0394 |
| 0.9118        | 25.72 | 8000  | 0.1292          | 0.2040 | 0.0384 |
| 0.8848        | 27.33 | 8500  | 0.1299          | 0.2028 | 0.0384 |
| 0.8667        | 28.94 | 9000  | 0.1228          | 0.1945 | 0.0367 |
| 0.8641        | 30.55 | 9500  | 0.1223          | 0.1939 | 0.0364 |
| 0.8516        | 32.15 | 10000 | 0.1184          | 0.1876 | 0.0349 |
| 0.8379        | 33.76 | 10500 | 0.1137          | 0.1821 | 0.0338 |
| 0.8235        | 35.37 | 11000 | 0.1127          | 0.1779 | 0.0331 |
| 0.8112        | 36.98 | 11500 | 0.1103          | 0.1766 | 0.0327 |
| 0.8069        | 38.59 | 12000 | 0.1092          | 0.1752 | 0.0323 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
