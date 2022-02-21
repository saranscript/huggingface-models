---
license: apache-2.0
language:
- as
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-as
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-as

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8318
- Wer: 0.5174

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
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.12
- num_epochs: 120

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.882         | 25.0  | 400  | 1.2290          | 0.8182 |
| 0.8275        | 50.0  | 800  | 0.6835          | 0.5398 |
| 0.337         | 75.0  | 1200 | 0.7789          | 0.5107 |
| 0.2113        | 100.0 | 1600 | 0.8318          | 0.5174 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

### Test Evaluation

Common Voice Assamese Test Set (v7.0)

- WER: 0.7224
- CER: 0.2882