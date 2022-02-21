---
language:
- sv-SE
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- sv
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Swedish - CV8 - v2
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 17.33
       - name: Test CER
         type: cer
         value: 5.8
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
         value: 27.01
       - name: Test CER
         type: cer
         value: 12.92
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SV-SE dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2779
- Wer: 0.2525

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
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

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.3224        | 1.37  | 500   | 3.3354          | 1.0    |
| 2.9318        | 2.74  | 1000  | 2.9361          | 1.0000 |
| 2.1371        | 4.11  | 1500  | 1.1157          | 0.8359 |
| 1.6883        | 5.48  | 2000  | 0.6003          | 0.6314 |
| 1.5812        | 6.85  | 2500  | 0.4746          | 0.4725 |
| 1.5145        | 8.22  | 3000  | 0.4376          | 0.4736 |
| 1.4763        | 9.59  | 3500  | 0.4006          | 0.3863 |
| 1.4215        | 10.96 | 4000  | 0.3783          | 0.3629 |
| 1.3638        | 12.33 | 4500  | 0.3555          | 0.3425 |
| 1.3561        | 13.7  | 5000  | 0.3340          | 0.3228 |
| 1.3406        | 15.07 | 5500  | 0.3373          | 0.3295 |
| 1.3055        | 16.44 | 6000  | 0.3432          | 0.3210 |
| 1.3048        | 17.81 | 6500  | 0.3282          | 0.3118 |
| 1.2863        | 19.18 | 7000  | 0.3226          | 0.3018 |
| 1.2389        | 20.55 | 7500  | 0.3050          | 0.2986 |
| 1.2361        | 21.92 | 8000  | 0.3048          | 0.2980 |
| 1.2263        | 23.29 | 8500  | 0.3011          | 0.2977 |
| 1.2225        | 24.66 | 9000  | 0.3017          | 0.2959 |
| 1.2044        | 26.03 | 9500  | 0.2977          | 0.2782 |
| 1.2017        | 27.4  | 10000 | 0.2966          | 0.2781 |
| 1.1912        | 28.77 | 10500 | 0.2999          | 0.2786 |
| 1.1658        | 30.14 | 11000 | 0.2991          | 0.2757 |
| 1.148         | 31.51 | 11500 | 0.2915          | 0.2684 |
| 1.1423        | 32.88 | 12000 | 0.2913          | 0.2643 |
| 1.123         | 34.25 | 12500 | 0.2777          | 0.2630 |
| 1.1297        | 35.62 | 13000 | 0.2873          | 0.2646 |
| 1.0987        | 36.98 | 13500 | 0.2829          | 0.2619 |
| 1.0873        | 38.36 | 14000 | 0.2864          | 0.2608 |
| 1.0848        | 39.73 | 14500 | 0.2827          | 0.2577 |
| 1.0628        | 41.1  | 15000 | 0.2896          | 0.2581 |
| 1.0815        | 42.47 | 15500 | 0.2814          | 0.2561 |
| 1.0587        | 43.83 | 16000 | 0.2738          | 0.2542 |
| 1.0709        | 45.21 | 16500 | 0.2785          | 0.2578 |
| 1.0512        | 46.57 | 17000 | 0.2793          | 0.2539 |
| 1.0396        | 47.94 | 17500 | 0.2788          | 0.2525 |
| 1.0481        | 49.31 | 18000 | 0.2777          | 0.2534 |

### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id patrickvonplaten/xls-r-300m-sv-cv8 --dataset mozilla-foundation/common_voice_8_0 --config sv-SE --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id patrickvonplaten/xls-r-300m-sv-cv8 --dataset speech-recognition-community-v2/dev_data --config sv --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.1+cu113
- Datasets 1.18.4.dev0
- Tokenizers 0.10.3
