---
license: apache-2.0
tags:
- generated_from_trainer
- bem
- robust-speech-event
model-index:
- name: wav2vec2-large-xls-r-1b-bemba-fds
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-1b-bemba-fds

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the [BembaSpeech](https://github.com/csikasote/BembaSpeech) dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2898
- Wer: 0.3435

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 8
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 15
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.7986        | 0.34  | 500  | 0.4549          | 0.7292 |
| 0.5358        | 0.67  | 1000 | 0.3325          | 0.4491 |
| 0.4559        | 1.01  | 1500 | 0.3090          | 0.3954 |
| 0.3983        | 1.35  | 2000 | 0.3067          | 0.4105 |
| 0.4067        | 1.68  | 2500 | 0.2838          | 0.3678 |
| 0.3722        | 2.02  | 3000 | 0.2824          | 0.3762 |
| 0.3286        | 2.36  | 3500 | 0.2810          | 0.3670 |
| 0.3239        | 2.69  | 4000 | 0.2643          | 0.3501 |
| 0.3187        | 3.03  | 4500 | 0.2838          | 0.3754 |
| 0.2801        | 3.36  | 5000 | 0.2815          | 0.3507 |
| 0.2806        | 3.7   | 5500 | 0.2725          | 0.3486 |
| 0.2714        | 4.04  | 6000 | 0.2898          | 0.3435 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
