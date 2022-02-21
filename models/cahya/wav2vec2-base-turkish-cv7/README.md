---
language:
- tr
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

This model is a fine-tuned version of [cahya/wav2vec2-base-turkish-artificial](https://huggingface.co/cahya/wav2vec2-base-turkish-artificial) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2893
- Wer: 0.2713

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
- train_batch_size: 128
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 512
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.8647        | 14.28 | 200  | 0.2758          | 0.2568 |
| 1.3376        | 28.56 | 400  | 0.2754          | 0.2722 |
| 1.1975        | 42.84 | 600  | 0.2929          | 0.2901 |
| 1.1024        | 57.14 | 800  | 0.2904          | 0.2928 |
| 1.0257        | 71.42 | 1000 | 0.2915          | 0.2823 |
| 0.9628        | 85.7  | 1200 | 0.2936          | 0.2749 |
| 0.9109        | 99.98 | 1400 | 0.2893          | 0.2713 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
