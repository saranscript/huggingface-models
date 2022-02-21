---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-tune_0.0005_8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-tune_0.0005_8

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5092
- Wer: 0.4821

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.5221        | 1.72  | 1000 | 1.6180          | 0.5266 |
| 1.3259        | 3.45  | 2000 | 1.4400          | 0.4921 |
| 1.1732        | 5.17  | 3000 | 1.3968          | 0.4669 |
| 1.0888        | 6.9   | 4000 | 1.3652          | 0.4569 |
| 0.9659        | 8.62  | 5000 | 1.3176          | 0.4332 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
