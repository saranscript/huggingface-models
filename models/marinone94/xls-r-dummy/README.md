---
language:
- sv-SE
license: cc0-1.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- mozilla-foundation/common_voice_8_0
- marinone94/nst_sv
model-index:
- name: XLS-R-300M - Swedish
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: mozilla-foundation/common_voice_8_0
      type: mozilla-foundation/common_voice_8_0
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 12.68
       - name: Test CER
         type: cer
         value: 3.79
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: speech-recognition-community-v2/dev_data
      type: speech-recognition-community-v2/dev_data
      args: sv
    metrics:
       - name: Test WER
         type: wer
         value: 27.55
       - name: Test CER
         type: cer
         value: 9.79
---

# 

This model is a fine-tuned version of [KBLab/wav2vec2-large-voxrex](https://huggingface.co/KBLab/wav2vec2-large-voxrex) on 2 epochs of the MARINONE94/NST_SV - SV dataset (80% random split with seed 42 as the dataset for now has only the "train" split), and then on 50 epochs of the the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SV-SE dataset ("train+validation" split).
See run.sh to have a complete overview of all the training steps.
NOTE: the first training for now didn't work as expected, so it might be useless or even degrade performance. Further investigation and development is needed.

It achieves the following results on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SV-SE "test" set, without any language model:
- Loss: 0.1497
- Wer: 0.1261

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.00025
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.3533        | 1.1   | 100  | 3.2807          | 1.0    |
| 3.1709        | 2.2   | 200  | 3.1325          | 1.0    |
| 3.0573        | 3.3   | 300  | 3.0615          | 1.0    |
| 3.0314        | 4.39  | 400  | 3.0990          | 1.0    |
| 3.0129        | 5.49  | 500  | 3.0400          | 1.0    |
| 2.9964        | 6.59  | 600  | 2.9990          | 1.0    |
| 2.9602        | 7.69  | 700  | 2.9620          | 1.0    |
| 2.8756        | 8.79  | 800  | 2.7302          | 1.0    |
| 2.2931        | 9.89  | 900  | 1.5058          | 0.9776 |
| 1.8427        | 10.98 | 1000 | 0.9155          | 0.7832 |
| 1.4286        | 12.09 | 1100 | 0.4075          | 0.3796 |
| 1.2229        | 13.19 | 1200 | 0.2893          | 0.2652 |
| 1.1106        | 14.28 | 1300 | 0.2469          | 0.2254 |
| 1.0663        | 15.38 | 1400 | 0.2219          | 0.1973 |
| 1.0667        | 16.48 | 1500 | 0.2129          | 0.1894 |
| 1.0193        | 17.58 | 1600 | 0.1991          | 0.1789 |
| 0.9816        | 18.68 | 1700 | 0.1940          | 0.1801 |
| 0.9814        | 19.78 | 1800 | 0.1860          | 0.1667 |
| 0.9787        | 20.87 | 1900 | 0.1888          | 0.1642 |
| 0.9699        | 21.97 | 2000 | 0.1875          | 0.1704 |
| 0.9616        | 23.08 | 2100 | 0.1802          | 0.1617 |
| 0.9378        | 24.17 | 2200 | 0.1793          | 0.1577 |
| 0.888         | 25.27 | 2300 | 0.1764          | 0.1545 |
| 0.8942        | 26.37 | 2400 | 0.1674          | 0.1492 |
| 0.8701        | 27.47 | 2500 | 0.1739          | 0.1512 |
| 0.8555        | 28.57 | 2600 | 0.1690          | 0.1446 |
| 0.8513        | 29.67 | 2700 | 0.1649          | 0.1477 |
| 0.8659        | 30.77 | 2800 | 0.1637          | 0.1422 |
| 0.8419        | 31.86 | 2900 | 0.1614          | 0.1397 |
| 0.8491        | 32.96 | 3000 | 0.1595          | 0.1401 |
| 0.8395        | 34.07 | 3100 | 0.1607          | 0.1376 |
| 0.83          | 35.16 | 3200 | 0.1538          | 0.1379 |
| 0.7835        | 36.26 | 3300 | 0.1602          | 0.1408 |
| 0.7703        | 37.36 | 3400 | 0.1601          | 0.1369 |
| 0.7474        | 38.46 | 3500 | 0.1514          | 0.1342 |
| 0.7719        | 39.56 | 3600 | 0.1593          | 0.1353 |
| 0.7638        | 40.66 | 3700 | 0.1536          | 0.1338 |
| 0.771         | 41.75 | 3800 | 0.1531          | 0.1317 |
| 0.7594        | 42.85 | 3900 | 0.1498          | 0.1288 |
| 0.7383        | 43.95 | 4000 | 0.1527          | 0.1300 |
| 0.7565        | 45.05 | 4100 | 0.1482          | 0.1289 |
| 0.7697        | 46.15 | 4200 | 0.1495          | 0.1272 |
| 0.7194        | 47.25 | 4300 | 0.1493          | 0.1269 |
| 0.7479        | 48.35 | 4400 | 0.1490          | 0.1276 |
| 0.7132        | 49.45 | 4500 | 0.1501          | 0.1265 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
