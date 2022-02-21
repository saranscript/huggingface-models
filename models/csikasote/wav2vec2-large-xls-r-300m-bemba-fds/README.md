---
license: apache-2.0
tags:
- generated_from_trainer
- bem
- robust-speech-event
model-index:
- name: wav2vec2-large-xls-r-300m-bemba-fds
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-bemba-fds

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the [BembaSpeech](https://github.com/csikasote/BembaSpeech) dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3594
- Wer: 0.3838

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9961        | 0.67  | 500  | 0.5157          | 0.7133 |
| 0.5903        | 1.34  | 1000 | 0.3663          | 0.4989 |
| 0.4804        | 2.02  | 1500 | 0.3547          | 0.4653 |
| 0.4146        | 2.69  | 2000 | 0.3274          | 0.4345 |
| 0.3792        | 3.36  | 2500 | 0.3586          | 0.4640 |
| 0.3509        | 4.03  | 3000 | 0.3360          | 0.4316 |
| 0.3114        | 4.7   | 3500 | 0.3382          | 0.4303 |
| 0.2935        | 5.38  | 4000 | 0.3263          | 0.4091 |
| 0.2723        | 6.05  | 4500 | 0.3348          | 0.4175 |
| 0.2502        | 6.72  | 5000 | 0.3317          | 0.4147 |
| 0.2334        | 7.39  | 5500 | 0.3542          | 0.4030 |
| 0.2287        | 8.06  | 6000 | 0.3594          | 0.4067 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
