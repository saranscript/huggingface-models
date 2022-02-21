---
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-spanish-small
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-spanish-small

This model is a fine-tuned version of [jhonparra18/wav2vec2-large-xls-r-300m-spanish-custom](https://huggingface.co/jhonparra18/wav2vec2-large-xls-r-300m-spanish-custom) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3596
- Wer: 0.2105

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.1971        | 0.79  | 400   | 0.2169          | 0.2077 |
| 0.2293        | 1.58  | 800   | 0.2507          | 0.2418 |
| 0.2065        | 2.37  | 1200  | 0.2703          | 0.2459 |
| 0.1842        | 3.16  | 1600  | 0.2716          | 0.2495 |
| 0.1634        | 3.95  | 2000  | 0.2695          | 0.2510 |
| 0.1443        | 4.74  | 2400  | 0.2754          | 0.2435 |
| 0.1345        | 5.53  | 2800  | 0.3119          | 0.2654 |
| 0.1267        | 6.32  | 3200  | 0.3154          | 0.2573 |
| 0.1237        | 7.11  | 3600  | 0.3251          | 0.2666 |
| 0.1118        | 7.91  | 4000  | 0.3139          | 0.2503 |
| 0.1051        | 8.7   | 4400  | 0.3286          | 0.2573 |
| 0.0964        | 9.49  | 4800  | 0.3348          | 0.2587 |
| 0.0946        | 10.28 | 5200  | 0.3357          | 0.2587 |
| 0.0897        | 11.07 | 5600  | 0.3408          | 0.2590 |
| 0.0812        | 11.86 | 6000  | 0.3380          | 0.2560 |
| 0.079         | 12.65 | 6400  | 0.3304          | 0.2415 |
| 0.0753        | 13.44 | 6800  | 0.3557          | 0.2540 |
| 0.0717        | 14.23 | 7200  | 0.3507          | 0.2519 |
| 0.0691        | 15.02 | 7600  | 0.3554          | 0.2587 |
| 0.0626        | 15.81 | 8000  | 0.3619          | 0.2520 |
| 0.0661        | 16.6  | 8400  | 0.3609          | 0.2564 |
| 0.0582        | 17.39 | 8800  | 0.3818          | 0.2520 |
| 0.0556        | 18.18 | 9200  | 0.3685          | 0.2410 |
| 0.0515        | 18.97 | 9600  | 0.3658          | 0.2367 |
| 0.0478        | 19.76 | 10000 | 0.3701          | 0.2413 |
| 0.0486        | 20.55 | 10400 | 0.3681          | 0.2371 |
| 0.0468        | 21.34 | 10800 | 0.3607          | 0.2370 |
| 0.0452        | 22.13 | 11200 | 0.3499          | 0.2286 |
| 0.0399        | 22.92 | 11600 | 0.3647          | 0.2282 |
| 0.0393        | 23.72 | 12000 | 0.3638          | 0.2255 |
| 0.0381        | 24.51 | 12400 | 0.3359          | 0.2202 |
| 0.0332        | 25.3  | 12800 | 0.3488          | 0.2177 |
| 0.033         | 26.09 | 13200 | 0.3628          | 0.2175 |
| 0.0311        | 26.88 | 13600 | 0.3695          | 0.2195 |
| 0.0294        | 27.67 | 14000 | 0.3624          | 0.2164 |
| 0.0281        | 28.46 | 14400 | 0.3688          | 0.2113 |
| 0.0274        | 29.25 | 14800 | 0.3596          | 0.2105 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
