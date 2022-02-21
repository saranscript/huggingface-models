---
language:
- ga-IE
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
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

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - GA-IE dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6569
- Wer: 0.8623

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.1851        | 15.62 | 500  | 1.8067          | 0.9256 |
| 2.1586        | 31.25 | 1000 | 1.7883          | 0.9180 |
| 2.0302        | 46.86 | 1500 | 1.7571          | 0.9192 |
| 1.8706        | 62.49 | 2000 | 1.6314          | 0.8858 |
| 1.7008        | 78.12 | 2500 | 1.6131          | 0.8679 |
| 1.4982        | 93.74 | 3000 | 1.6540          | 0.8650 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
