---
language:
- mn
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - MN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7192
- Wer: 0.4503

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 400
- num_epochs: 60.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 6.35  | 400  | 0.8067          | 0.7164 |
| 2.7613        | 12.7  | 800  | 0.6799          | 0.5861 |
| 0.7592        | 19.05 | 1200 | 0.6560          | 0.5425 |
| 0.5883        | 25.4  | 1600 | 0.6494          | 0.5206 |
| 0.4996        | 31.75 | 2000 | 0.6838          | 0.5085 |
| 0.4996        | 38.1  | 2400 | 0.6754          | 0.4913 |
| 0.4189        | 44.44 | 2800 | 0.7176          | 0.4837 |
| 0.359         | 50.79 | 3200 | 0.7055          | 0.4680 |
| 0.3068        | 57.14 | 3600 | 0.7192          | 0.4554 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
