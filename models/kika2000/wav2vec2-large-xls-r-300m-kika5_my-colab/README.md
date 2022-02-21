---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-kika5_my-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-kika5_my-colab

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3860
- Wer: 0.3505

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
- lr_scheduler_warmup_steps: 500
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.0007        | 4.82  | 400  | 0.6696          | 0.8283 |
| 0.2774        | 9.64  | 800  | 0.4231          | 0.5476 |
| 0.1182        | 14.46 | 1200 | 0.4253          | 0.5102 |
| 0.0859        | 19.28 | 1600 | 0.4600          | 0.4866 |
| 0.0693        | 24.1  | 2000 | 0.4030          | 0.4533 |
| 0.0611        | 28.92 | 2400 | 0.4189          | 0.4412 |
| 0.0541        | 33.73 | 2800 | 0.4272          | 0.4380 |
| 0.0478        | 38.55 | 3200 | 0.4537          | 0.4505 |
| 0.0428        | 43.37 | 3600 | 0.4349          | 0.4181 |
| 0.038         | 48.19 | 4000 | 0.4562          | 0.4199 |
| 0.0345        | 53.01 | 4400 | 0.4209          | 0.4310 |
| 0.0316        | 57.83 | 4800 | 0.4336          | 0.4058 |
| 0.0288        | 62.65 | 5200 | 0.4004          | 0.3920 |
| 0.025         | 67.47 | 5600 | 0.4115          | 0.3857 |
| 0.0225        | 72.29 | 6000 | 0.4296          | 0.3948 |
| 0.0182        | 77.11 | 6400 | 0.3963          | 0.3772 |
| 0.0165        | 81.93 | 6800 | 0.3921          | 0.3687 |
| 0.0152        | 86.75 | 7200 | 0.3969          | 0.3592 |
| 0.0133        | 91.57 | 7600 | 0.3803          | 0.3527 |
| 0.0118        | 96.39 | 8000 | 0.3860          | 0.3505 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
