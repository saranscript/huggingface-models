---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: egy-slang-model
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# egy-slang-model

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.9273
- Wer: 1.0000

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 1.64  | 200  | 2.9735          | 1.0    |
| 3.8098        | 3.28  | 400  | 2.9765          | 1.0    |
| 3.8098        | 4.91  | 600  | 2.9662          | 1.0    |
| 2.9531        | 6.56  | 800  | 2.9708          | 1.0    |
| 2.9531        | 8.2   | 1000 | 2.9673          | 1.0    |
| 2.9259        | 9.83  | 1200 | 2.9989          | 1.0    |
| 2.9259        | 11.47 | 1400 | 2.9889          | 1.0    |
| 2.9023        | 13.11 | 1600 | 2.9739          | 1.0    |
| 2.9023        | 14.75 | 1800 | 3.0040          | 1.0000 |
| 2.8832        | 16.39 | 2000 | 3.0170          | 1.0    |
| 2.8832        | 18.03 | 2200 | 2.9963          | 0.9999 |
| 2.8691        | 19.67 | 2400 | 2.9273          | 1.0000 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.1
- Datasets 1.13.3
- Tokenizers 0.10.3
