---
language:
- tr
license: apache-2.0
tags:
- speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-common_voice-tr-demo
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-common_voice-tr-demo-dist

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3856
- Wer: 0.3581
- Cer: 0.0805

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
- train_batch_size: 4
- num_gpus: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 1
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 15.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.7391        | 0.92  | 100  | 3.5760          | 1.0    |
| 2.927         | 1.83  | 200  | 3.0796          | 0.9999 |
| 0.9009        | 2.75  | 300  | 0.9278          | 0.8226 |
| 0.6529        | 3.67  | 400  | 0.5926          | 0.6367 |
| 0.3623        | 4.59  | 500  | 0.5372          | 0.5692 |
| 0.2888        | 5.5   | 600  | 0.4407          | 0.4838 |
| 0.285         | 6.42  | 700  | 0.4341          | 0.4694 |
| 0.0842        | 7.34  | 800  | 0.4153          | 0.4302 |
| 0.1415        | 8.26  | 900  | 0.4317          | 0.4136 |
| 0.1552        | 9.17  | 1000 | 0.4145          | 0.4013 |
| 0.1184        | 10.09 | 1100 | 0.4115          | 0.3844 |
| 0.0556        | 11.01 | 1200 | 0.4182          | 0.3862 |
| 0.0851        | 11.93 | 1300 | 0.3985          | 0.3688 |
| 0.0961        | 12.84 | 1400 | 0.4030          | 0.3665 |
| 0.0596        | 13.76 | 1500 | 0.3880          | 0.3631 |
| 0.0359        | 14.68 | 1600 | 0.3878          | 0.3589 |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
