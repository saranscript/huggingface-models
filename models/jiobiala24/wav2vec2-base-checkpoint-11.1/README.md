---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-base-checkpoint-11.1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-checkpoint-11.1

This model is a fine-tuned version of [jiobiala24/wav2vec2-base-checkpoint-10](https://huggingface.co/jiobiala24/wav2vec2-base-checkpoint-10) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0173
- Wer: 0.3350

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
| 0.2788        | 1.52  | 1000  | 0.5776          | 0.3410 |
| 0.2277        | 3.04  | 2000  | 0.6148          | 0.3465 |
| 0.1772        | 4.56  | 3000  | 0.6497          | 0.3497 |
| 0.1528        | 6.08  | 4000  | 0.6786          | 0.3430 |
| 0.1285        | 7.6   | 5000  | 0.6779          | 0.3489 |
| 0.1104        | 9.12  | 6000  | 0.7417          | 0.3528 |
| 0.0965        | 10.64 | 7000  | 0.7956          | 0.3477 |
| 0.0914        | 12.16 | 8000  | 0.7994          | 0.3570 |
| 0.082         | 13.68 | 9000  | 0.8690          | 0.3510 |
| 0.0788        | 15.2  | 10000 | 0.8569          | 0.3526 |
| 0.0727        | 16.72 | 11000 | 0.8885          | 0.3440 |
| 0.0656        | 18.24 | 12000 | 0.9586          | 0.3476 |
| 0.0608        | 19.76 | 13000 | 0.9317          | 0.3495 |
| 0.0588        | 21.28 | 14000 | 0.9809          | 0.3449 |
| 0.0547        | 22.8  | 15000 | 0.9552          | 0.3421 |
| 0.0519        | 24.32 | 16000 | 0.9782          | 0.3380 |
| 0.0474        | 25.84 | 17000 | 0.9923          | 0.3386 |
| 0.046         | 27.36 | 18000 | 0.9984          | 0.3347 |
| 0.045         | 28.88 | 19000 | 1.0173          | 0.3350 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
