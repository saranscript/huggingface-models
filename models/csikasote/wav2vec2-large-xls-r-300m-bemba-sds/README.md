---
license: apache-2.0
tags:
- generated_from_trainer
- bem
- robust-speech-event
model-index:
- name: wav2vec2-large-xls-r-300m-bemba-sds
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-bemba-sds

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the [BembaSpeech](https://github.com/csikasote/BembaSpeech) dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5579
- Wer: 0.3981
- Cer: 0.0921

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
| 1.1625        | 0.66  | 500  | 0.5109          | 0.6940 |
| 0.5286        | 1.31  | 1000 | 0.3892          | 0.4965 |
| 0.4575        | 1.97  | 1500 | 0.3361          | 0.4500 |
| 0.3955        | 2.62  | 2000 | 0.3089          | 0.4109 |
| 0.36          | 3.28  | 2500 | 0.3068          | 0.4128 |
| 0.3427        | 3.93  | 3000 | 0.2977          | 0.3937 |
| 0.2986        | 4.59  | 3500 | 0.2966          | 0.3769 |
| 0.2885        | 5.24  | 4000 | 0.2892          | 0.3756 |
| 0.2674        | 5.9   | 4500 | 0.2905          | 0.3545 |
| 0.2457        | 6.55  | 5000 | 0.2938          | 0.3683 |
| 0.2327        | 7.21  | 5500 | 0.2982          | 0.3560 |
| 0.2195        | 7.86  | 6000 | 0.2793          | 0.3501 |
| 0.1947        | 8.52  | 6500 | 0.2788          | 0.3434 |
| 0.1969        | 9.17  | 7000 | 0.2874          | 0.3387 |
| 0.1765        | 9.83  | 7500 | 0.2813          | 0.3429 |
| 0.1718        | 10.48 | 8000 | 0.2991          | 0.3446 |
| 0.3761        | 11.14 | 8500 | 0.5579          | 0.5680 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
