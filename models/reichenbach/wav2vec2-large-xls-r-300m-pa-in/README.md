---
license: apache-2.0
language:
- pa
- pa-IN
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-pa-in
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-pa-in

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9680
- Wer: 0.7283

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 180
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 8.2615        | 24.97  | 400  | 3.4784          | 1.0    |
| 3.366         | 49.97  | 800  | 2.3662          | 0.9917 |
| 1.1678        | 74.97  | 1200 | 1.4806          | 0.7709 |
| 0.5496        | 99.97  | 1600 | 1.7166          | 0.7476 |
| 0.4101        | 124.97 | 2000 | 1.8473          | 0.7510 |
| 0.3317        | 149.97 | 2400 | 1.9177          | 0.7322 |
| 0.2956        | 174.97 | 2800 | 1.9680          | 0.7283 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3


### Evaluations Result

- WER: 0.7539
- CER: 0.2928