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

This model is a fine-tuned version of [facebook/wav2vec2-base-960h](https://huggingface.co/facebook/wav2vec2-base-960h) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2368
- Wer: 0.8655

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
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
| 10.7111       | 4.0   | 500  | 6.1429          | 1.0    |
| 4.8905        | 8.0   | 1000 | 6.0597          | 1.0    |
| 3.4516        | 12.0  | 1500 | 3.0125          | 1.0    |
| 2.9895        | 16.0  | 2000 | 2.9629          | 1.0    |
| 2.9155        | 20.0  | 2500 | 2.4479          | 1.0    |
| 2.3186        | 24.0  | 3000 | 1.5888          | 0.9565 |
| 1.8469        | 28.0  | 3500 | 1.2368          | 0.8655 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
