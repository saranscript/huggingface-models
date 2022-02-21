---
language:
- pt
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- pt
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
license: apache-2.0
model-index:
- name: wav2vec2-xls-r-pt-cv7-from-bp400h
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 12.13
       - name: Test CER
         type: cer
         value: 3.68
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
         value: 28.23
       - name: Test CER
         type: cer
         value: 12.58
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-pt-cv7-from-bp400h

This model is a fine-tuned version of [lgris/bp_400h_xlsr2_300M](https://huggingface.co/lgris/bp_400h_xlsr2_300M) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1535
- Wer: 0.1254

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- training_steps: 5000

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.4991        | 0.13  | 100  | 0.1774          | 0.1464 |
| 0.4655        | 0.26  | 200  | 0.1884          | 0.1568 |
| 0.4689        | 0.39  | 300  | 0.2282          | 0.1672 |
| 0.4662        | 0.52  | 400  | 0.1997          | 0.1584 |
| 0.4592        | 0.65  | 500  | 0.1989          | 0.1663 |
| 0.4533        | 0.78  | 600  | 0.2004          | 0.1698 |
| 0.4391        | 0.91  | 700  | 0.1888          | 0.1642 |
| 0.4655        | 1.04  | 800  | 0.1921          | 0.1624 |
| 0.4138        | 1.17  | 900  | 0.1950          | 0.1602 |
| 0.374         | 1.3   | 1000 | 0.2077          | 0.1658 |
| 0.4064        | 1.43  | 1100 | 0.1945          | 0.1596 |
| 0.3922        | 1.56  | 1200 | 0.2069          | 0.1665 |
| 0.4226        | 1.69  | 1300 | 0.1962          | 0.1573 |
| 0.3974        | 1.82  | 1400 | 0.1919          | 0.1553 |
| 0.3631        | 1.95  | 1500 | 0.1854          | 0.1573 |
| 0.3797        | 2.08  | 1600 | 0.1902          | 0.1550 |
| 0.3287        | 2.21  | 1700 | 0.1926          | 0.1598 |
| 0.3568        | 2.34  | 1800 | 0.1888          | 0.1534 |
| 0.3415        | 2.47  | 1900 | 0.1834          | 0.1502 |
| 0.3545        | 2.6   | 2000 | 0.1906          | 0.1560 |
| 0.3344        | 2.73  | 2100 | 0.1804          | 0.1524 |
| 0.3308        | 2.86  | 2200 | 0.1741          | 0.1485 |
| 0.344         | 2.99  | 2300 | 0.1787          | 0.1455 |
| 0.309         | 3.12  | 2400 | 0.1773          | 0.1448 |
| 0.312         | 3.25  | 2500 | 0.1738          | 0.1440 |
| 0.3066        | 3.38  | 2600 | 0.1727          | 0.1417 |
| 0.2999        | 3.51  | 2700 | 0.1692          | 0.1436 |
| 0.2985        | 3.64  | 2800 | 0.1732          | 0.1430 |
| 0.3058        | 3.77  | 2900 | 0.1754          | 0.1402 |
| 0.2943        | 3.9   | 3000 | 0.1691          | 0.1379 |
| 0.2813        | 4.03  | 3100 | 0.1754          | 0.1376 |
| 0.2733        | 4.16  | 3200 | 0.1639          | 0.1363 |
| 0.2592        | 4.29  | 3300 | 0.1675          | 0.1349 |
| 0.2697        | 4.42  | 3400 | 0.1618          | 0.1360 |
| 0.2538        | 4.55  | 3500 | 0.1658          | 0.1348 |
| 0.2746        | 4.67  | 3600 | 0.1674          | 0.1325 |
| 0.2655        | 4.8   | 3700 | 0.1655          | 0.1319 |
| 0.2745        | 4.93  | 3800 | 0.1665          | 0.1316 |
| 0.2617        | 5.06  | 3900 | 0.1600          | 0.1311 |
| 0.2674        | 5.19  | 4000 | 0.1623          | 0.1311 |
| 0.237         | 5.32  | 4100 | 0.1591          | 0.1315 |
| 0.2669        | 5.45  | 4200 | 0.1584          | 0.1295 |
| 0.2476        | 5.58  | 4300 | 0.1572          | 0.1285 |
| 0.2445        | 5.71  | 4400 | 0.1580          | 0.1271 |
| 0.2207        | 5.84  | 4500 | 0.1567          | 0.1269 |
| 0.2289        | 5.97  | 4600 | 0.1536          | 0.1260 |
| 0.2438        | 6.1   | 4700 | 0.1530          | 0.1260 |
| 0.227         | 6.23  | 4800 | 0.1544          | 0.1249 |
| 0.2256        | 6.36  | 4900 | 0.1543          | 0.1254 |
| 0.2184        | 6.49  | 5000 | 0.1535          | 0.1254 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
