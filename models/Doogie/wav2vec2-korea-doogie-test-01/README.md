---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
  name: wav2vec2-korea-doogie-test-01
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-korea-doogie-test-01

This model is a fine-tuned version of [Doogie/wav2vec2-korea-doogie-test-01](https://huggingface.co/Doogie/wav2vec2-korea-doogie-test-01) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4207
- Wer: 0.5938

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
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.1594        | 2.38  | 500   | 1.2825          | 0.6134 |
| 0.1272        | 4.76  | 1000  | 1.3252          | 0.6271 |
| 0.1291        | 7.14  | 1500  | 1.3236          | 0.6158 |
| 0.1192        | 9.52  | 2000  | 1.3589          | 0.6384 |
| 0.0981        | 11.9  | 2500  | 1.3778          | 0.6425 |
| 0.0946        | 14.29 | 3000  | 1.4500          | 0.6336 |
| 0.0854        | 16.67 | 3500  | 1.4169          | 0.6164 |
| 0.0766        | 19.05 | 4000  | 1.3665          | 0.6217 |
| 0.0676        | 21.43 | 4500  | 1.4593          | 0.6348 |
| 0.0631        | 23.81 | 5000  | 1.5267          | 0.6188 |
| 0.0627        | 26.19 | 5500  | 1.4988          | 0.6306 |
| 0.059         | 28.57 | 6000  | 1.4986          | 0.6265 |
| 0.0502        | 30.95 | 6500  | 1.4268          | 0.6158 |
| 0.0496        | 33.33 | 7000  | 1.3859          | 0.5998 |
| 0.0418        | 35.71 | 7500  | 1.4154          | 0.6057 |
| 0.0376        | 38.1  | 8000  | 1.4077          | 0.6116 |
| 0.0374        | 40.48 | 8500  | 1.4164          | 0.6087 |
| 0.0301        | 42.86 | 9000  | 1.4634          | 0.6152 |
| 0.0289        | 45.24 | 9500  | 1.4360          | 0.6045 |
| 0.0283        | 47.62 | 10000 | 1.4213          | 0.5998 |
| 0.0228        | 50.0  | 10500 | 1.4207          | 0.5938 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu113
- Datasets 1.16.1
- Tokenizers 0.10.3
