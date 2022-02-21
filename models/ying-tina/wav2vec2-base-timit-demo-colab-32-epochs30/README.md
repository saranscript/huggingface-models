---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-base-timit-demo-colab-32-epochs30
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-timit-demo-colab-32-epochs30

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4615
- Wer: 0.3434

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
| 3.5243        | 4.0   | 500  | 1.4532          | 0.9540 |
| 0.6178        | 8.0   | 1000 | 0.5490          | 0.4627 |
| 0.223         | 12.0  | 1500 | 0.4513          | 0.3881 |
| 0.1299        | 16.0  | 2000 | 0.4573          | 0.3698 |
| 0.0875        | 20.0  | 2500 | 0.4950          | 0.3637 |
| 0.0613        | 24.0  | 3000 | 0.4327          | 0.3479 |
| 0.0478        | 28.0  | 3500 | 0.4615          | 0.3434 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
