---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-base-timit-demo-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-timit-demo-colab

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4798
- Wer: 0.3474

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
| 3.5229        | 4.0   | 500  | 1.6557          | 1.0422 |
| 0.6618        | 8.0   | 1000 | 0.4420          | 0.4469 |
| 0.2211        | 12.0  | 1500 | 0.4705          | 0.4002 |
| 0.1281        | 16.0  | 2000 | 0.4347          | 0.3688 |
| 0.0868        | 20.0  | 2500 | 0.4653          | 0.3590 |
| 0.062         | 24.0  | 3000 | 0.4747          | 0.3519 |
| 0.0472        | 28.0  | 3500 | 0.4798          | 0.3474 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.9.0+cu102
- Datasets 1.17.0
- Tokenizers 0.10.3
