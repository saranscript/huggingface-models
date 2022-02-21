---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-cv8-da
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-cv8-da

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5955
- Wer: 0.3546

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 4e-05
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 500
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 3.8131        | 5.55   | 300  | 3.2631          | 1.0    |
| 3.0248        | 11.11  | 600  | 2.9593          | 1.0    |
| 2.9104        | 16.66  | 900  | 2.6911          | 1.0    |
| 1.3248        | 22.22  | 1200 | 0.9344          | 0.6874 |
| 0.753         | 27.77  | 1500 | 0.6279          | 0.5060 |
| 0.5252        | 33.33  | 1800 | 0.5370          | 0.4466 |
| 0.4108        | 38.88  | 2100 | 0.5006          | 0.4228 |
| 0.3366        | 44.44  | 2400 | 0.4805          | 0.3989 |
| 0.3015        | 49.99  | 2700 | 0.4979          | 0.3972 |
| 0.2593        | 55.55  | 3000 | 0.4976          | 0.3868 |
| 0.2267        | 61.11  | 3300 | 0.5049          | 0.3827 |
| 0.2086        | 66.66  | 3600 | 0.5075          | 0.3739 |
| 0.1899        | 72.22  | 3900 | 0.5285          | 0.3701 |
| 0.1847        | 77.77  | 4200 | 0.5259          | 0.3727 |
| 0.1597        | 83.33  | 4500 | 0.5424          | 0.3693 |
| 0.1503        | 88.88  | 4800 | 0.5169          | 0.3636 |
| 0.1463        | 94.44  | 5100 | 0.5558          | 0.3674 |
| 0.1436        | 99.99  | 5400 | 0.5728          | 0.3744 |
| 0.131         | 105.55 | 5700 | 0.5758          | 0.3665 |
| 0.1226        | 111.11 | 6000 | 0.5906          | 0.3648 |
| 0.1136        | 116.66 | 6300 | 0.5807          | 0.3621 |
| 0.1053        | 122.22 | 6600 | 0.6074          | 0.3605 |
| 0.1007        | 127.77 | 6900 | 0.5780          | 0.3593 |
| 0.0972        | 133.33 | 7200 | 0.5892          | 0.3552 |
| 0.0912        | 138.88 | 7500 | 0.5921          | 0.3518 |
| 0.0861        | 144.44 | 7800 | 0.6320          | 0.3600 |
| 0.0877        | 149.99 | 8100 | 0.6299          | 0.3553 |
| 0.0939        | 155.55 | 8400 | 0.6412          | 0.3624 |
| 0.0772        | 161.11 | 8700 | 0.6223          | 0.3555 |
| 0.0815        | 166.66 | 9000 | 0.5955          | 0.3546 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
