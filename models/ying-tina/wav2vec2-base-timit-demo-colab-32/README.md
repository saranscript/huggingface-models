---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
  name: wav2vec2-base-timit-demo-colab-32
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-timit-demo-colab-32

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4488
- Wer: 0.3149

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

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.6155        | 4.0   | 500  | 2.2647          | 0.9992 |
| 0.9037        | 8.0   | 1000 | 0.4701          | 0.4336 |
| 0.3159        | 12.0  | 1500 | 0.4247          | 0.3575 |
| 0.1877        | 16.0  | 2000 | 0.4477          | 0.3442 |
| 0.1368        | 20.0  | 2500 | 0.4932          | 0.3384 |
| 0.1062        | 24.0  | 3000 | 0.4758          | 0.3202 |
| 0.0928        | 28.0  | 3500 | 0.4488          | 0.3149 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Tokenizers 0.10.3
