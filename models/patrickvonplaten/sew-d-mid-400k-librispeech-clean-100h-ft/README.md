---
license: apache-2.0
tags:
- automatic-speech-recognition
- librispeech_asr
- generated_from_trainer
model-index:
- name: sew-d-mid-400k-librispeech-clean-100h-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-d-mid-400k-librispeech-clean-100h-ft

This model is a fine-tuned version of [asapp/sew-d-mid-400k](https://huggingface.co/asapp/sew-d-mid-400k) on the LIBRISPEECH_ASR - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3540
- Wer: 1.0536

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 32
- total_eval_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 7.319         | 0.11  | 100  | 11.0572         | 1.0    |
| 3.6726        | 0.22  | 200  | 4.2003          | 1.0    |
| 2.981         | 0.34  | 300  | 3.5742          | 0.9919 |
| 2.9411        | 0.45  | 400  | 3.2599          | 1.0    |
| 2.903         | 0.56  | 500  | 2.9350          | 1.0    |
| 2.8597        | 0.67  | 600  | 2.9514          | 1.0    |
| 2.7771        | 0.78  | 700  | 2.8521          | 1.0    |
| 2.7926        | 0.9   | 800  | 2.7821          | 1.0120 |
| 2.6623        | 1.01  | 900  | 2.7027          | 0.9924 |
| 2.5893        | 1.12  | 1000 | 2.6667          | 1.0240 |
| 2.5733        | 1.23  | 1100 | 2.6341          | 1.0368 |
| 2.5455        | 1.35  | 1200 | 2.5928          | 1.0411 |
| 2.4919        | 1.46  | 1300 | 2.5695          | 1.0817 |
| 2.5182        | 1.57  | 1400 | 2.5559          | 1.1072 |
| 2.4766        | 1.68  | 1500 | 2.5229          | 1.1257 |
| 2.4267        | 1.79  | 1600 | 2.4991          | 1.1151 |
| 2.3919        | 1.91  | 1700 | 2.4768          | 1.1139 |
| 2.3883        | 2.02  | 1800 | 2.4452          | 1.0636 |
| 2.3737        | 2.13  | 1900 | 2.4304          | 1.0594 |
| 2.3569        | 2.24  | 2000 | 2.4095          | 1.0539 |
| 2.3641        | 2.35  | 2100 | 2.3997          | 1.0511 |
| 2.3281        | 2.47  | 2200 | 2.3856          | 1.0414 |
| 2.2912        | 2.58  | 2300 | 2.3750          | 1.0696 |
| 2.3028        | 2.69  | 2400 | 2.3684          | 1.0436 |
| 2.2906        | 2.8   | 2500 | 2.3613          | 1.0538 |
| 2.2822        | 2.91  | 2600 | 2.3558          | 1.0506 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.13.4.dev0
- Tokenizers 0.10.3
