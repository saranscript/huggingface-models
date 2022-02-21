---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-large-xlsr-53_english
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-53_english

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2620
- Wer: 0.1916

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.0506        | 0.12  | 250   | 3.0206          | 0.9999 |
| 1.4381        | 0.25  | 500   | 1.0267          | 0.6323 |
| 1.0903        | 0.37  | 750   | 0.5841          | 0.3704 |
| 1.0384        | 0.5   | 1000  | 0.5156          | 0.3348 |
| 0.9658        | 0.62  | 1250  | 0.4721          | 0.3221 |
| 0.9184        | 0.74  | 1500  | 0.4301          | 0.3213 |
| 0.8939        | 0.87  | 1750  | 0.4188          | 0.2884 |
| 0.9051        | 0.99  | 2000  | 0.3852          | 0.2807 |
| 0.563         | 1.12  | 2250  | 0.3752          | 0.2804 |
| 0.6122        | 1.24  | 2500  | 0.3745          | 0.2732 |
| 0.6213        | 1.36  | 2750  | 0.3671          | 0.2575 |
| 0.5839        | 1.49  | 3000  | 0.3560          | 0.2578 |
| 0.615         | 1.61  | 3250  | 0.3555          | 0.2536 |
| 0.5557        | 1.74  | 3500  | 0.3511          | 0.2485 |
| 0.5497        | 1.86  | 3750  | 0.3364          | 0.2425 |
| 0.5412        | 1.98  | 4000  | 0.3253          | 0.2418 |
| 0.2834        | 2.11  | 4250  | 0.3293          | 0.2322 |
| 0.2723        | 2.23  | 4500  | 0.3157          | 0.2322 |
| 0.2713        | 2.35  | 4750  | 0.3148          | 0.2304 |
| 0.2878        | 2.48  | 5000  | 0.3143          | 0.2286 |
| 0.2776        | 2.6   | 5250  | 0.3122          | 0.2250 |
| 0.2553        | 2.73  | 5500  | 0.3003          | 0.2234 |
| 0.278         | 2.85  | 5750  | 0.2973          | 0.2198 |
| 0.2445        | 2.97  | 6000  | 0.2938          | 0.2180 |
| 0.4361        | 3.1   | 6250  | 0.2914          | 0.2132 |
| 0.3979        | 3.22  | 6500  | 0.2916          | 0.2125 |
| 0.4221        | 3.35  | 6750  | 0.2879          | 0.2113 |
| 0.4051        | 3.47  | 7000  | 0.2819          | 0.2100 |
| 0.4218        | 3.59  | 7250  | 0.2812          | 0.2072 |
| 0.4201        | 3.72  | 7500  | 0.2772          | 0.2055 |
| 0.3515        | 3.84  | 7750  | 0.2747          | 0.2031 |
| 0.4021        | 3.97  | 8000  | 0.2702          | 0.2018 |
| 0.4304        | 4.09  | 8250  | 0.2721          | 0.2007 |
| 0.3923        | 4.21  | 8500  | 0.2689          | 0.1991 |
| 0.3824        | 4.34  | 8750  | 0.2692          | 0.1980 |
| 0.3743        | 4.46  | 9000  | 0.2718          | 0.1950 |
| 0.3771        | 4.59  | 9250  | 0.2653          | 0.1950 |
| 0.4048        | 4.71  | 9500  | 0.2649          | 0.1934 |
| 0.3539        | 4.83  | 9750  | 0.2638          | 0.1919 |
| 0.3498        | 4.96  | 10000 | 0.2620          | 0.1916 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.1+cu113
- Datasets 1.17.0
- Tokenizers 0.10.3
