---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xlsr-53-rm-vallader-with-lm
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xlsr-53-rm-vallader-with-lm

This model is a fine-tuned version of [anuragshas/wav2vec2-large-xlsr-53-rm-vallader](https://huggingface.co/anuragshas/wav2vec2-large-xlsr-53-rm-vallader) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4552
- Wer: 0.3206

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.112
- num_epochs: 30

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.2379        | 3.12  | 100  | 0.4041          | 0.3396 |
| 0.103         | 6.25  | 200  | 0.4400          | 0.3337 |
| 0.0664        | 9.38  | 300  | 0.4239          | 0.3315 |
| 0.0578        | 12.5  | 400  | 0.4303          | 0.3267 |
| 0.0446        | 15.62 | 500  | 0.4575          | 0.3274 |
| 0.041         | 18.75 | 600  | 0.4451          | 0.3223 |
| 0.0402        | 21.88 | 700  | 0.4507          | 0.3206 |
| 0.0374        | 25.0  | 800  | 0.4649          | 0.3208 |
| 0.0371        | 28.12 | 900  | 0.4552          | 0.3206 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.10.3
