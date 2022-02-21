---
language:
- ro
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-ro-300M
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ro
    metrics:
       - name: Test WER (without LM)
         type: wer
         value: 22.47
       - name: Test CER (without LM)
         type: cer
         value: 5.98
       - name: Test WER (with LM)
         type: wer
         value: 14.25
       - name: Test CER (with LM)
         type: cer
         value: 4.54
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-ro-300M

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - RO dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3459
- Wer: 0.2246
- Cer: 0.0599

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 3
- total_train_batch_size: 48
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 3.286         | 0.88  | 500   | 2.2888          | 1.0314 | 0.6265 |
| 1.4473        | 1.76  | 1000  | 0.9654          | 0.8807 | 0.2998 |
| 0.9565        | 2.65  | 1500  | 0.6621          | 0.7223 | 0.2157 |
| 0.7691        | 3.53  | 2000  | 0.5976          | 0.6276 | 0.1810 |
| 0.643         | 4.41  | 2500  | 0.4970          | 0.5335 | 0.1478 |
| 0.5632        | 5.29  | 3000  | 0.4524          | 0.4922 | 0.1360 |
| 0.5066        | 6.17  | 3500  | 0.4501          | 0.4538 | 0.1250 |
| 0.4551        | 7.05  | 4000  | 0.4211          | 0.4480 | 0.1209 |
| 0.4178        | 7.94  | 4500  | 0.4053          | 0.4158 | 0.1130 |
| 0.386         | 8.82  | 5000  | 0.3839          | 0.3988 | 0.1090 |
| 0.3654        | 9.7   | 5500  | 0.3828          | 0.3843 | 0.1050 |
| 0.3366        | 10.58 | 6000  | 0.3863          | 0.3758 | 0.1014 |
| 0.3248        | 11.46 | 6500  | 0.3710          | 0.3733 | 0.1021 |
| 0.3108        | 12.35 | 7000  | 0.3665          | 0.3610 | 0.0985 |
| 0.2986        | 13.23 | 7500  | 0.3804          | 0.3527 | 0.0960 |
| 0.2849        | 14.11 | 8000  | 0.3630          | 0.3395 | 0.0919 |
| 0.2732        | 14.99 | 8500  | 0.3636          | 0.3363 | 0.0913 |
| 0.2622        | 15.87 | 9000  | 0.3671          | 0.3270 | 0.0893 |
| 0.2493        | 16.75 | 9500  | 0.3790          | 0.3338 | 0.0897 |
| 0.2449        | 17.64 | 10000 | 0.3494          | 0.3208 | 0.0872 |
| 0.2344        | 18.52 | 10500 | 0.3734          | 0.3189 | 0.0860 |
| 0.2267        | 19.4  | 11000 | 0.3662          | 0.3128 | 0.0834 |
| 0.2238        | 20.28 | 11500 | 0.3471          | 0.3046 | 0.0821 |
| 0.2153        | 21.16 | 12000 | 0.3567          | 0.3011 | 0.0807 |
| 0.2105        | 22.05 | 12500 | 0.3628          | 0.2982 | 0.0800 |
| 0.2009        | 22.93 | 13000 | 0.3306          | 0.2882 | 0.0765 |
| 0.1975        | 23.81 | 13500 | 0.3562          | 0.2976 | 0.0796 |
| 0.1907        | 24.69 | 14000 | 0.3618          | 0.2881 | 0.0776 |
| 0.1839        | 25.57 | 14500 | 0.3798          | 0.2997 | 0.0809 |
| 0.1825        | 26.45 | 15000 | 0.3629          | 0.2846 | 0.0770 |
| 0.1783        | 27.34 | 15500 | 0.3468          | 0.2703 | 0.0729 |
| 0.1726        | 28.22 | 16000 | 0.3492          | 0.2777 | 0.0739 |
| 0.1681        | 29.1  | 16500 | 0.3442          | 0.2733 | 0.0734 |
| 0.1641        | 29.98 | 17000 | 0.3621          | 0.2794 | 0.0753 |
| 0.1579        | 30.86 | 17500 | 0.3499          | 0.2646 | 0.0720 |
| 0.1537        | 31.75 | 18000 | 0.3604          | 0.2658 | 0.0730 |
| 0.1525        | 32.63 | 18500 | 0.3489          | 0.2597 | 0.0703 |
| 0.1451        | 33.51 | 19000 | 0.3589          | 0.2600 | 0.0696 |
| 0.1418        | 34.39 | 19500 | 0.3404          | 0.2503 | 0.0665 |
| 0.1391        | 35.27 | 20000 | 0.3538          | 0.2521 | 0.0667 |
| 0.1333        | 36.16 | 20500 | 0.3368          | 0.2461 | 0.0652 |
| 0.1314        | 37.04 | 21000 | 0.3596          | 0.2536 | 0.0678 |
| 0.1267        | 37.92 | 21500 | 0.3485          | 0.2482 | 0.0658 |
| 0.1239        | 38.8  | 22000 | 0.3501          | 0.2434 | 0.0648 |
| 0.1198        | 39.68 | 22500 | 0.3603          | 0.2418 | 0.0651 |
| 0.1167        | 40.56 | 23000 | 0.3492          | 0.2388 | 0.0638 |
| 0.1153        | 41.45 | 23500 | 0.3465          | 0.2389 | 0.0640 |
| 0.1107        | 42.33 | 24000 | 0.3525          | 0.2357 | 0.0632 |
| 0.1085        | 43.21 | 24500 | 0.3547          | 0.2342 | 0.0631 |
| 0.1076        | 44.09 | 25000 | 0.3499          | 0.2308 | 0.0621 |
| 0.1026        | 44.97 | 25500 | 0.3462          | 0.2297 | 0.0615 |
| 0.1008        | 45.85 | 26000 | 0.3457          | 0.2300 | 0.0607 |
| 0.0983        | 46.74 | 26500 | 0.3429          | 0.2265 | 0.0604 |
| 0.099         | 47.62 | 27000 | 0.3472          | 0.2273 | 0.0610 |
| 0.094         | 48.5  | 27500 | 0.3442          | 0.2255 | 0.0605 |
| 0.0923        | 49.38 | 28000 | 0.3464          | 0.2247 | 0.0601 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
