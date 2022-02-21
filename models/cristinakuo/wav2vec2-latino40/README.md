---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-latino40
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-latino40

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.8795
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
- lr_scheduler_warmup_steps: 100
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer |
|:-------------:|:-----:|:----:|:---------------:|:---:|
| 5.6846        | 0.83  | 100  | 2.9086          | 1.0 |
| 2.8686        | 1.67  | 200  | 2.8922          | 1.0 |
| 2.8805        | 2.5   | 300  | 2.9326          | 1.0 |
| 2.8613        | 3.33  | 400  | 2.8698          | 1.0 |
| 2.8643        | 4.17  | 500  | 2.9027          | 1.0 |
| 2.8688        | 5.0   | 600  | 2.9544          | 1.0 |
| 2.8689        | 5.83  | 700  | 2.8914          | 1.0 |
| 2.8558        | 6.67  | 800  | 2.8762          | 1.0 |
| 2.8537        | 7.5   | 900  | 2.8982          | 1.0 |
| 2.8522        | 8.33  | 1000 | 2.8820          | 1.0 |
| 2.8468        | 9.17  | 1100 | 2.8760          | 1.0 |
| 2.8454        | 10.0  | 1200 | 2.8795          | 1.0 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.9.1
- Datasets 1.16.1
- Tokenizers 0.10.3
