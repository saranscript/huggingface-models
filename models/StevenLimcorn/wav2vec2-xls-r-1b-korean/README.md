---
language: ko
license: apache-2.0
tags:
  - automatic-speech-recognition
  - robust-speech-event
  - generated_from_trainer
datasets:
  - kresnik/zeroth_korean
model-index:
- name: 'Wav2Vec2 XLS-R Korean 1B'
  results: 
    - task:
        name: Automatic Speech Recognition
        type: automatic-speech-recognition
      dataset:
        name: Zeroth Korean
        type: kresnik/zeroth_korean
        args: clean
      metrics:
        - name: Test WER
          type: wer
          value: 8.62
        - name: Test CER
          type: cer
          value: 2.24
    - task:
        name: Automatic Speech Recognition
        type: automatic-speech-recognition
      dataset:
        name: Robust Speech Event - Dev Data
        type: speech-recognition-community-v2/dev_data
        args: ko
      metrics:
        - name: Test WER
          type: wer
          value: 88.402
        - name: Test CER
          type: cer
          value: 48.74
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the KRESNIK/ZEROTH_KOREAN - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0960
- Wer: 0.0862
- Cer: 0.0224

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0002
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 3.765         | 0.72  | 500   | 2.5988          | 0.9742 | 0.5570 |
| 2.4829        | 1.44  | 1000  | 1.2169          | 0.7622 | 0.2989 |
| 2.522         | 2.16  | 1500  | 1.1796          | 0.7810 | 0.3164 |
| 2.5122        | 2.88  | 2000  | 1.1773          | 0.8269 | 0.3537 |
| 2.4101        | 3.6   | 2500  | 1.1751          | 0.7762 | 0.3263 |
| 2.3391        | 4.32  | 3000  | 1.0176          | 0.7320 | 0.2853 |
| 2.2714        | 5.04  | 3500  | 0.9985          | 0.7351 | 0.2883 |
| 2.1833        | 5.75  | 4000  | 0.8875          | 0.7005 | 0.2598 |
| 2.1531        | 6.47  | 4500  | 0.9157          | 0.6907 | 0.2628 |
| 2.1019        | 7.19  | 5000  | 0.9093          | 0.7043 | 0.2626 |
| 2.0943        | 7.91  | 5500  | 0.8949          | 0.7095 | 0.2635 |
| 2.0285        | 8.63  | 6000  | 0.8583          | 0.6894 | 0.2551 |
| 1.9057        | 9.35  | 6500  | 0.7278          | 0.6176 | 0.2094 |
| 1.8583        | 10.07 | 7000  | 0.8197          | 0.6605 | 0.2401 |
| 1.8095        | 10.79 | 7500  | 0.6592          | 0.5983 | 0.1971 |
| 1.7588        | 11.51 | 8000  | 0.6004          | 0.5572 | 0.1767 |
| 1.702         | 12.23 | 8500  | 0.6145          | 0.5580 | 0.1795 |
| 1.6375        | 12.95 | 9000  | 0.5200          | 0.5364 | 0.1628 |
| 1.6138        | 13.67 | 9500  | 0.5244          | 0.5186 | 0.1590 |
| 1.5441        | 14.39 | 10000 | 0.5044          | 0.5211 | 0.1552 |
| 1.4886        | 15.11 | 10500 | 0.4284          | 0.4585 | 0.1328 |
| 1.4136        | 15.83 | 11000 | 0.4393          | 0.4644 | 0.1351 |
| 1.39          | 16.55 | 11500 | 0.4154          | 0.4410 | 0.1273 |
| 1.3509        | 17.27 | 12000 | 0.3821          | 0.4169 | 0.1171 |
| 1.3161        | 17.98 | 12500 | 0.3506          | 0.4091 | 0.1086 |
| 1.259         | 18.7  | 13000 | 0.3359          | 0.3819 | 0.1031 |
| 1.2426        | 19.42 | 13500 | 0.3289          | 0.3744 | 0.1010 |
| 1.197         | 20.14 | 14000 | 0.3267          | 0.3688 | 0.0977 |
| 1.1884        | 20.86 | 14500 | 0.3111          | 0.3555 | 0.0931 |
| 1.1479        | 21.58 | 15000 | 0.3059          | 0.3479 | 0.0931 |
| 1.0864        | 22.3  | 15500 | 0.2783          | 0.3300 | 0.0849 |
| 1.0763        | 23.02 | 16000 | 0.2566          | 0.2937 | 0.0752 |
| 1.0521        | 23.74 | 16500 | 0.2568          | 0.2986 | 0.0771 |
| 1.012         | 24.46 | 17000 | 0.2448          | 0.2921 | 0.0738 |
| 0.9831        | 25.18 | 17500 | 0.2330          | 0.2753 | 0.0682 |
| 0.9575        | 25.9  | 18000 | 0.2231          | 0.2723 | 0.0675 |
| 0.9325        | 26.62 | 18500 | 0.2307          | 0.2857 | 0.0720 |
| 0.8867        | 27.34 | 19000 | 0.2031          | 0.2446 | 0.0603 |
| 0.8793        | 28.06 | 19500 | 0.2095          | 0.2481 | 0.0615 |
| 0.8382        | 28.78 | 20000 | 0.1893          | 0.2199 | 0.0538 |
| 0.79          | 29.5  | 20500 | 0.1800          | 0.2122 | 0.0509 |
| 0.7761        | 30.22 | 21000 | 0.1719          | 0.2064 | 0.0489 |
| 0.7911        | 30.93 | 21500 | 0.1707          | 0.1950 | 0.0485 |
| 0.7413        | 31.65 | 22000 | 0.1631          | 0.1915 | 0.0464 |
| 0.7186        | 32.37 | 22500 | 0.1583          | 0.1753 | 0.0426 |
| 0.712         | 33.09 | 23000 | 0.1477          | 0.1752 | 0.0427 |
| 0.693         | 33.81 | 23500 | 0.1522          | 0.1725 | 0.0419 |
| 0.6692        | 34.53 | 24000 | 0.1549          | 0.1702 | 0.0408 |
| 0.6409        | 35.25 | 24500 | 0.1439          | 0.1548 | 0.0378 |
| 0.6464        | 35.97 | 25000 | 0.1422          | 0.1534 | 0.0373 |
| 0.6192        | 36.69 | 25500 | 0.1375          | 0.1489 | 0.0364 |
| 0.5924        | 37.41 | 26000 | 0.1278          | 0.1367 | 0.0330 |
| 0.5757        | 38.13 | 26500 | 0.1269          | 0.1278 | 0.0324 |
| 0.565         | 38.85 | 27000 | 0.1242          | 0.1306 | 0.0319 |
| 0.5326        | 39.57 | 27500 | 0.1228          | 0.1373 | 0.0338 |
| 0.5218        | 40.29 | 28000 | 0.1251          | 0.1326 | 0.0324 |
| 0.5248        | 41.01 | 28500 | 0.1205          | 0.1184 | 0.0294 |
| 0.5027        | 41.73 | 29000 | 0.1128          | 0.1087 | 0.0276 |
| 0.4775        | 42.45 | 29500 | 0.1117          | 0.1071 | 0.0270 |
| 0.4765        | 43.17 | 30000 | 0.1055          | 0.1036 | 0.0265 |
| 0.4626        | 43.88 | 30500 | 0.1046          | 0.1045 | 0.0268 |
| 0.4411        | 44.6  | 31000 | 0.1035          | 0.1045 | 0.0270 |
| 0.4351        | 45.32 | 31500 | 0.0996          | 0.0929 | 0.0244 |
| 0.4358        | 46.04 | 32000 | 0.1017          | 0.0947 | 0.0241 |
| 0.4185        | 46.76 | 32500 | 0.0982          | 0.0903 | 0.0235 |
| 0.4178        | 47.48 | 33000 | 0.0983          | 0.0892 | 0.0230 |
| 0.4038        | 48.2  | 33500 | 0.0981          | 0.0895 | 0.0230 |
| 0.3876        | 48.92 | 34000 | 0.0968          | 0.0888 | 0.0225 |
| 0.3879        | 49.64 | 34500 | 0.0958          | 0.0862 | 0.0221 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
