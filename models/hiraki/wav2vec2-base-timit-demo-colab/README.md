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
- Loss: 3.3780
- Wer: 1.0

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
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 0.08  | 10   | 14.0985         | 1.0    |
| No log        | 0.16  | 20   | 13.8638         | 1.0004 |
| No log        | 0.24  | 30   | 13.5135         | 1.0023 |
| No log        | 0.32  | 40   | 12.8708         | 1.0002 |
| No log        | 0.4   | 50   | 11.6927         | 1.0    |
| No log        | 0.48  | 60   | 10.2733         | 1.0    |
| No log        | 0.56  | 70   | 8.1396          | 1.0    |
| No log        | 0.64  | 80   | 5.3503          | 1.0    |
| No log        | 0.72  | 90   | 3.7975          | 1.0    |
| No log        | 0.8   | 100  | 3.4275          | 1.0    |
| No log        | 0.88  | 110  | 3.3596          | 1.0    |
| No log        | 0.96  | 120  | 3.3780          | 1.0    |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
