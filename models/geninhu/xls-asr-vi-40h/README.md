---
license: apache-2.0
language:
- vi
tags:
- automatic-speech-recognition
- robust-speech-event
- common-voice
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: xls-asr-vi-40h
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7.0
      type: mozilla-foundation/common_voice_7_0

      args: vi
    metrics:
       - name: Test WER (with Language model)
         type: wer
         value: 56.57
---

# xls-asr-vi-40h

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common voice 7.0 vi & private dataset.
It achieves the following results on the evaluation set (Without Language Model):
- Loss: 1.1177
- Wer: 60.58

## Evaluation
Please run the eval.py file

```bash
!python eval_custom.py --model_id geninhu/xls-asr-vi-40h --dataset mozilla-foundation/common_voice_7_0 --config vi --split test
```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-06
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 23.3878       | 0.93  | 1500  | 21.9179         | 1.0    |
| 8.8862        | 1.85  | 3000  | 6.0599          | 1.0    |
| 4.3701        | 2.78  | 4500  | 4.3837          | 1.0    |
| 4.113         | 3.7   | 6000  | 4.2698          | 0.9982 |
| 3.9666        | 4.63  | 7500  | 3.9726          | 0.9989 |
| 3.5965        | 5.56  | 9000  | 3.7124          | 0.9975 |
| 3.3944        | 6.48  | 10500 | 3.5005          | 1.0057 |
| 3.304         | 7.41  | 12000 | 3.3710          | 1.0043 |
| 3.2482        | 8.33  | 13500 | 3.4201          | 1.0155 |
| 3.212         | 9.26  | 15000 | 3.3732          | 1.0151 |
| 3.1778        | 10.19 | 16500 | 3.2763          | 1.0009 |
| 3.1027        | 11.11 | 18000 | 3.1943          | 1.0025 |
| 2.9905        | 12.04 | 19500 | 2.8082          | 0.9703 |
| 2.7095        | 12.96 | 21000 | 2.4993          | 0.9302 |
| 2.4862        | 13.89 | 22500 | 2.3072          | 0.9140 |
| 2.3271        | 14.81 | 24000 | 2.1398          | 0.8949 |
| 2.1968        | 15.74 | 25500 | 2.0594          | 0.8817 |
| 2.111         | 16.67 | 27000 | 1.9404          | 0.8630 |
| 2.0387        | 17.59 | 28500 | 1.8895          | 0.8497 |
| 1.9504        | 18.52 | 30000 | 1.7961          | 0.8315 |
| 1.9039        | 19.44 | 31500 | 1.7433          | 0.8213 |
| 1.8342        | 20.37 | 33000 | 1.6790          | 0.7994 |
| 1.7824        | 21.3  | 34500 | 1.6291          | 0.7825 |
| 1.7359        | 22.22 | 36000 | 1.5783          | 0.7706 |
| 1.7053        | 23.15 | 37500 | 1.5248          | 0.7492 |
| 1.6504        | 24.07 | 39000 | 1.4930          | 0.7406 |
| 1.6263        | 25.0  | 40500 | 1.4572          | 0.7348 |
| 1.5893        | 25.93 | 42000 | 1.4202          | 0.7161 |
| 1.5669        | 26.85 | 43500 | 1.3987          | 0.7143 |
| 1.5277        | 27.78 | 45000 | 1.3512          | 0.6991 |
| 1.501         | 28.7  | 46500 | 1.3320          | 0.6879 |
| 1.4781        | 29.63 | 48000 | 1.3112          | 0.6788 |
| 1.4477        | 30.56 | 49500 | 1.2850          | 0.6657 |
| 1.4483        | 31.48 | 51000 | 1.2813          | 0.6633 |
| 1.4065        | 32.41 | 52500 | 1.2475          | 0.6541 |
| 1.3779        | 33.33 | 54000 | 1.2244          | 0.6503 |
| 1.3788        | 34.26 | 55500 | 1.2116          | 0.6407 |
| 1.3428        | 35.19 | 57000 | 1.1938          | 0.6352 |
| 1.3453        | 36.11 | 58500 | 1.1927          | 0.6340 |
| 1.3137        | 37.04 | 60000 | 1.1699          | 0.6252 |
| 1.2984        | 37.96 | 61500 | 1.1666          | 0.6229 |
| 1.2927        | 38.89 | 63000 | 1.1585          | 0.6188 |
| 1.2919        | 39.81 | 64500 | 1.1618          | 0.6190 |
| 1.293         | 40.74 | 66000 | 1.1479          | 0.6181 |
| 1.2853        | 41.67 | 67500 | 1.1423          | 0.6202 |
| 1.2687        | 42.59 | 69000 | 1.1315          | 0.6131 |
| 1.2603        | 43.52 | 70500 | 1.1333          | 0.6128 |
| 1.2577        | 44.44 | 72000 | 1.1191          | 0.6079 |
| 1.2435        | 45.37 | 73500 | 1.1177          | 0.6079 |
| 1.251         | 46.3  | 75000 | 1.1211          | 0.6092 |
| 1.2482        | 47.22 | 76500 | 1.1177          | 0.6060 |
| 1.2422        | 48.15 | 78000 | 1.1227          | 0.6097 |
| 1.2485        | 49.07 | 79500 | 1.1187          | 0.6071 |
| 1.2425        | 50.0  | 81000 | 1.1177          | 0.6058 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
