---
language:
- pt
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- pt
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: wavlm-large-CORAA-pt-cv7
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wavlm-large-CORAA-pt-cv7

This model is a fine-tuned version of [lgris/WavLM-large-CORAA-pt](https://huggingface.co/lgris/WavLM-large-CORAA-pt) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2546
- Wer: 0.2261

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
| 0.6029        | 0.13  | 100  | 0.3679          | 0.3347 |
| 0.5297        | 0.26  | 200  | 0.3516          | 0.3227 |
| 0.5134        | 0.39  | 300  | 0.3327          | 0.3167 |
| 0.4941        | 0.52  | 400  | 0.3281          | 0.3122 |
| 0.4816        | 0.65  | 500  | 0.3154          | 0.3102 |
| 0.4649        | 0.78  | 600  | 0.3199          | 0.3058 |
| 0.461         | 0.91  | 700  | 0.3047          | 0.2974 |
| 0.4613        | 1.04  | 800  | 0.3006          | 0.2900 |
| 0.4198        | 1.17  | 900  | 0.2951          | 0.2891 |
| 0.3864        | 1.3   | 1000 | 0.2989          | 0.2862 |
| 0.3963        | 1.43  | 1100 | 0.2932          | 0.2830 |
| 0.3953        | 1.56  | 1200 | 0.2936          | 0.2829 |
| 0.3962        | 1.69  | 1300 | 0.2952          | 0.2773 |
| 0.3811        | 1.82  | 1400 | 0.2915          | 0.2748 |
| 0.3736        | 1.95  | 1500 | 0.2839          | 0.2684 |
| 0.3507        | 2.08  | 1600 | 0.2914          | 0.2678 |
| 0.3277        | 2.21  | 1700 | 0.2895          | 0.2652 |
| 0.3344        | 2.34  | 1800 | 0.2843          | 0.2673 |
| 0.335         | 2.47  | 1900 | 0.2821          | 0.2635 |
| 0.3559        | 2.6   | 2000 | 0.2830          | 0.2599 |
| 0.3254        | 2.73  | 2100 | 0.2711          | 0.2577 |
| 0.3263        | 2.86  | 2200 | 0.2685          | 0.2546 |
| 0.3266        | 2.99  | 2300 | 0.2679          | 0.2521 |
| 0.3066        | 3.12  | 2400 | 0.2727          | 0.2526 |
| 0.2998        | 3.25  | 2500 | 0.2648          | 0.2537 |
| 0.2961        | 3.38  | 2600 | 0.2630          | 0.2519 |
| 0.3046        | 3.51  | 2700 | 0.2684          | 0.2506 |
| 0.3006        | 3.64  | 2800 | 0.2604          | 0.2492 |
| 0.2992        | 3.77  | 2900 | 0.2682          | 0.2508 |
| 0.2775        | 3.9   | 3000 | 0.2732          | 0.2440 |
| 0.2903        | 4.03  | 3100 | 0.2659          | 0.2427 |
| 0.2535        | 4.16  | 3200 | 0.2650          | 0.2433 |
| 0.2714        | 4.29  | 3300 | 0.2588          | 0.2394 |
| 0.2636        | 4.42  | 3400 | 0.2652          | 0.2434 |
| 0.2647        | 4.55  | 3500 | 0.2624          | 0.2371 |
| 0.2796        | 4.67  | 3600 | 0.2611          | 0.2373 |
| 0.2644        | 4.8   | 3700 | 0.2604          | 0.2341 |
| 0.2657        | 4.93  | 3800 | 0.2567          | 0.2331 |
| 0.2423        | 5.06  | 3900 | 0.2594          | 0.2322 |
| 0.2556        | 5.19  | 4000 | 0.2587          | 0.2323 |
| 0.2327        | 5.32  | 4100 | 0.2639          | 0.2299 |
| 0.2613        | 5.45  | 4200 | 0.2569          | 0.2310 |
| 0.2382        | 5.58  | 4300 | 0.2585          | 0.2298 |
| 0.2404        | 5.71  | 4400 | 0.2543          | 0.2287 |
| 0.2368        | 5.84  | 4500 | 0.2553          | 0.2286 |
| 0.2514        | 5.97  | 4600 | 0.2517          | 0.2279 |
| 0.2415        | 6.1   | 4700 | 0.2524          | 0.2270 |
| 0.2338        | 6.23  | 4800 | 0.2540          | 0.2265 |
| 0.219         | 6.36  | 4900 | 0.2549          | 0.2263 |
| 0.2428        | 6.49  | 5000 | 0.2546          | 0.2261 |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
