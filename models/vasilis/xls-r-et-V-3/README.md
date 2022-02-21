---
language:
- et
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- et
- robust-speech-event
- generated_from_trainer
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: 'XLS-R-1B - Estonian'
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: et
    metrics:
       - name: Test WER
         type: wer
         value: 52.47
       - name: Test CER
         type: cer
         value: 12.59
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
         value: 61.02
       - name: Test CER
         type: cer
         value: 21.08
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ET dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8824
- Wer: 0.5246

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
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- training_steps: 25000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 1.0296        | 2.79   | 500   | 0.8106          | 0.8029 |
| 0.9339        | 5.59   | 1000  | 0.7419          | 0.7932 |
| 0.8925        | 8.38   | 1500  | 0.7137          | 0.7706 |
| 0.8484        | 11.17  | 2000  | 0.7020          | 0.7677 |
| 0.7521        | 13.97  | 2500  | 0.7043          | 0.7375 |
| 0.719         | 16.76  | 3000  | 0.6617          | 0.7428 |
| 0.656         | 19.55  | 3500  | 0.6388          | 0.7202 |
| 0.6085        | 22.35  | 4000  | 0.6211          | 0.6960 |
| 0.5598        | 25.14  | 4500  | 0.6132          | 0.6644 |
| 0.4969        | 27.93  | 5000  | 0.6065          | 0.6521 |
| 0.4638        | 30.73  | 5500  | 0.6978          | 0.6577 |
| 0.4385        | 33.52  | 6000  | 0.5994          | 0.6565 |
| 0.396         | 36.31  | 6500  | 0.6170          | 0.6258 |
| 0.3861        | 39.11  | 7000  | 0.6486          | 0.6217 |
| 0.3602        | 41.9   | 7500  | 0.6508          | 0.6115 |
| 0.3251        | 44.69  | 8000  | 0.7022          | 0.6253 |
| 0.3197        | 47.49  | 8500  | 0.7706          | 0.6215 |
| 0.3013        | 50.28  | 9000  | 0.6419          | 0.5999 |
| 0.2813        | 53.07  | 9500  | 0.6908          | 0.5959 |
| 0.286         | 55.87  | 10000 | 0.7151          | 0.5916 |
| 0.2645        | 58.66  | 10500 | 0.7181          | 0.5860 |
| 0.2535        | 61.45  | 11000 | 0.7877          | 0.5979 |
| 0.247         | 64.25  | 11500 | 0.8199          | 0.6129 |
| 0.2412        | 67.04  | 12000 | 0.7679          | 0.5884 |
| 0.2404        | 69.83  | 12500 | 0.7266          | 0.5816 |
| 0.2293        | 72.63  | 13000 | 0.7928          | 0.5795 |
| 0.2176        | 75.42  | 13500 | 0.7916          | 0.5846 |
| 0.2143        | 78.21  | 14000 | 0.7954          | 0.5765 |
| 0.2185        | 81.01  | 14500 | 0.8317          | 0.5907 |
| 0.2057        | 83.8   | 15000 | 0.8016          | 0.5851 |
| 0.1895        | 86.59  | 15500 | 0.8080          | 0.5679 |
| 0.1883        | 89.39  | 16000 | 0.8103          | 0.5712 |
| 0.1802        | 92.18  | 16500 | 0.8383          | 0.5644 |
| 0.1826        | 94.97  | 17000 | 0.8799          | 0.5657 |
| 0.1717        | 97.77  | 17500 | 0.8620          | 0.5709 |
| 0.1701        | 100.56 | 18000 | 0.8717          | 0.5662 |
| 0.1623        | 103.35 | 18500 | 0.8534          | 0.5594 |
| 0.158         | 106.15 | 19000 | 0.8595          | 0.5546 |
| 0.1508        | 108.94 | 19500 | 0.8574          | 0.5545 |
| 0.142         | 111.73 | 20000 | 0.8671          | 0.5537 |
| 0.1395        | 114.53 | 20500 | 0.8436          | 0.5525 |
| 0.1373        | 117.32 | 21000 | 0.8808          | 0.5482 |
| 0.1338        | 120.11 | 21500 | 0.9024          | 0.5418 |
| 0.1278        | 122.91 | 22000 | 0.9143          | 0.5409 |
| 0.1207        | 125.7  | 22500 | 0.8917          | 0.5358 |
| 0.1203        | 128.49 | 23000 | 0.9041          | 0.5341 |
| 0.1083        | 131.28 | 23500 | 0.8884          | 0.5341 |
| 0.1147        | 134.08 | 24000 | 0.8910          | 0.5255 |
| 0.1129        | 136.87 | 24500 | 0.8826          | 0.5241 |
| 0.1029        | 139.66 | 25000 | 0.8824          | 0.5246 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
