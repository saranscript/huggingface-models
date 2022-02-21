---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-base-checkpoint-9
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-checkpoint-9

This model is a fine-tuned version of [jiobiala24/wav2vec2-base-checkpoint-8](https://huggingface.co/jiobiala24/wav2vec2-base-checkpoint-8) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9203
- Wer: 0.3258

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
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.2783        | 1.58  | 1000  | 0.5610          | 0.3359 |
| 0.2251        | 3.16  | 2000  | 0.5941          | 0.3374 |
| 0.173         | 4.74  | 3000  | 0.6026          | 0.3472 |
| 0.1475        | 6.32  | 4000  | 0.6750          | 0.3482 |
| 0.1246        | 7.9   | 5000  | 0.6673          | 0.3414 |
| 0.1081        | 9.48  | 6000  | 0.7072          | 0.3409 |
| 0.1006        | 11.06 | 7000  | 0.7413          | 0.3392 |
| 0.0879        | 12.64 | 8000  | 0.7831          | 0.3394 |
| 0.0821        | 14.22 | 9000  | 0.7371          | 0.3333 |
| 0.0751        | 15.8  | 10000 | 0.8321          | 0.3445 |
| 0.0671        | 17.38 | 11000 | 0.8362          | 0.3357 |
| 0.0646        | 18.96 | 12000 | 0.8709          | 0.3367 |
| 0.0595        | 20.54 | 13000 | 0.8352          | 0.3321 |
| 0.0564        | 22.12 | 14000 | 0.8854          | 0.3323 |
| 0.052         | 23.7  | 15000 | 0.9031          | 0.3315 |
| 0.0485        | 25.28 | 16000 | 0.9171          | 0.3278 |
| 0.046         | 26.86 | 17000 | 0.9390          | 0.3254 |
| 0.0438        | 28.44 | 18000 | 0.9203          | 0.3258 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
