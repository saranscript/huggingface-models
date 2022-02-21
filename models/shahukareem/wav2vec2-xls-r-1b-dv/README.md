---
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- dv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-1b-dv
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: dv
    metrics:
       - name: Test WER
         type: wer
         value: 21.32
       - name: Test CER
         type: cer
         value: 3.43
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-1b-dv

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1702
- Wer: 0.2123

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 4.5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.8412        | 0.66  | 400   | 0.7160          | 0.7913 |
| 0.6832        | 1.33  | 800   | 0.3401          | 0.5268 |
| 0.4624        | 1.99  | 1200  | 0.2671          | 0.4683 |
| 0.3832        | 2.65  | 1600  | 0.2395          | 0.4410 |
| 0.3443        | 3.32  | 2000  | 0.2410          | 0.4296 |
| 0.324         | 3.98  | 2400  | 0.2302          | 0.4143 |
| 0.2934        | 4.64  | 2800  | 0.2402          | 0.4136 |
| 0.2773        | 5.31  | 3200  | 0.2134          | 0.4088 |
| 0.2638        | 5.97  | 3600  | 0.2072          | 0.4037 |
| 0.2479        | 6.63  | 4000  | 0.2036          | 0.3876 |
| 0.2424        | 7.3   | 4400  | 0.2037          | 0.3767 |
| 0.2249        | 7.96  | 4800  | 0.1959          | 0.3802 |
| 0.2169        | 8.62  | 5200  | 0.1943          | 0.3813 |
| 0.2109        | 9.29  | 5600  | 0.1944          | 0.3691 |
| 0.1991        | 9.95  | 6000  | 0.1870          | 0.3589 |
| 0.1917        | 10.61 | 6400  | 0.1834          | 0.3485 |
| 0.1862        | 11.28 | 6800  | 0.1857          | 0.3486 |
| 0.1744        | 11.94 | 7200  | 0.1812          | 0.3330 |
| 0.171         | 12.6  | 7600  | 0.1797          | 0.3436 |
| 0.1599        | 13.27 | 8000  | 0.1839          | 0.3319 |
| 0.1597        | 13.93 | 8400  | 0.1737          | 0.3385 |
| 0.1494        | 14.59 | 8800  | 0.1807          | 0.3239 |
| 0.1444        | 15.26 | 9200  | 0.1750          | 0.3155 |
| 0.1382        | 15.92 | 9600  | 0.1705          | 0.3084 |
| 0.1299        | 16.58 | 10000 | 0.1777          | 0.2999 |
| 0.1306        | 17.25 | 10400 | 0.1765          | 0.3056 |
| 0.1239        | 17.91 | 10800 | 0.1676          | 0.2864 |
| 0.1149        | 18.57 | 11200 | 0.1774          | 0.2861 |
| 0.1134        | 19.24 | 11600 | 0.1654          | 0.2699 |
| 0.1101        | 19.9  | 12000 | 0.1621          | 0.2651 |
| 0.1038        | 20.56 | 12400 | 0.1686          | 0.2610 |
| 0.1038        | 21.23 | 12800 | 0.1722          | 0.2559 |
| 0.0988        | 21.89 | 13200 | 0.1708          | 0.2486 |
| 0.0949        | 22.55 | 13600 | 0.1696          | 0.2453 |
| 0.0913        | 23.22 | 14000 | 0.1677          | 0.2424 |
| 0.0879        | 23.88 | 14400 | 0.1640          | 0.2359 |
| 0.0888        | 24.54 | 14800 | 0.1697          | 0.2347 |
| 0.0826        | 25.21 | 15200 | 0.1709          | 0.2314 |
| 0.0819        | 25.87 | 15600 | 0.1679          | 0.2256 |
| 0.0793        | 26.53 | 16000 | 0.1701          | 0.2214 |
| 0.0773        | 27.2  | 16400 | 0.1682          | 0.2176 |
| 0.0783        | 27.86 | 16800 | 0.1685          | 0.2165 |
| 0.074         | 28.52 | 17200 | 0.1688          | 0.2155 |
| 0.0753        | 29.19 | 17600 | 0.1695          | 0.2110 |
| 0.0699        | 29.85 | 18000 | 0.1702          | 0.2123 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
