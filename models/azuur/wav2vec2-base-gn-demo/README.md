---
license: apache-2.0
language:
- gn
tags:
- generated_from_trainer
- mozilla-foundation/common_voice_8_0
- robust-speech-event
datasets:
- common_voice
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-base-gn-demo
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-gn-demo

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7426
- Wer: 0.7256

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 50
- num_epochs: 60
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 4.0   | 100  | 0.7045          | 0.7409 |
| No log        | 8.0   | 200  | 0.7200          | 0.75   |
| No log        | 12.0  | 300  | 0.7400          | 0.7439 |
| No log        | 16.0  | 400  | 0.7677          | 0.7515 |
| 0.0846        | 20.0  | 500  | 0.7765          | 0.7271 |
| 0.0846        | 24.0  | 600  | 0.7821          | 0.7287 |
| 0.0846        | 28.0  | 700  | 0.7671          | 0.7180 |
| 0.0846        | 32.0  | 800  | 0.7594          | 0.7180 |
| 0.0846        | 36.0  | 900  | 0.7500          | 0.7165 |
| 0.0713        | 40.0  | 1000 | 0.7351          | 0.7287 |
| 0.0713        | 44.0  | 1100 | 0.7361          | 0.7241 |
| 0.0713        | 48.0  | 1200 | 0.7389          | 0.7378 |
| 0.0713        | 52.0  | 1300 | 0.7424          | 0.7210 |
| 0.0713        | 56.0  | 1400 | 0.7425          | 0.7256 |
| 0.0669        | 60.0  | 1500 | 0.7426          | 0.7256 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.10.3
