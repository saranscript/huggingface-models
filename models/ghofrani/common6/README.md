---
language:
- fa
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: common6
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# common6

This model is a fine-tuned version of [common6/checkpoint-3500](https://huggingface.co/common6/checkpoint-3500) on the COMMON_VOICE - FA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3706
- Wer: 0.3421

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 6e-05
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 256
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 200.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.0344        | 10.0  | 500   | 0.4043          | 0.4511 |
| 0.9651        | 20.0  | 1000  | 0.3793          | 0.4159 |
| 0.9125        | 30.0  | 1500  | 0.3756          | 0.4046 |
| 0.8831        | 40.0  | 2000  | 0.3650          | 0.3876 |
| 0.8399        | 50.0  | 2500  | 0.3605          | 0.3772 |
| 0.819         | 60.0  | 3000  | 0.3622          | 0.3714 |
| 0.8029        | 70.0  | 3500  | 0.3561          | 0.3664 |
| 0.8104        | 80.0  | 4000  | 0.3595          | 0.3660 |
| 0.8118        | 90.0  | 4500  | 0.3460          | 0.3592 |
| 0.7831        | 100.0 | 5000  | 0.3566          | 0.3593 |
| 0.744         | 110.0 | 5500  | 0.3578          | 0.3535 |
| 0.7388        | 120.0 | 6000  | 0.3538          | 0.3520 |
| 0.714         | 130.0 | 6500  | 0.3682          | 0.3506 |
| 0.7291        | 140.0 | 7000  | 0.3625          | 0.3505 |
| 0.697         | 150.0 | 7500  | 0.3619          | 0.3479 |
| 0.6811        | 160.0 | 8000  | 0.3631          | 0.3440 |
| 0.6841        | 170.0 | 8500  | 0.3672          | 0.3460 |
| 0.6616        | 180.0 | 9000  | 0.3677          | 0.3410 |
| 0.6471        | 190.0 | 9500  | 0.3707          | 0.3420 |
| 0.6759        | 200.0 | 10000 | 0.3706          | 0.3421 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.3.dev0
- Tokenizers 0.10.3
