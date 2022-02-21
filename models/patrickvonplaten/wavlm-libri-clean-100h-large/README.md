---
tags:
- automatic-speech-recognition
- librispeech_asr
- generated_from_trainer
- wavlm_libri_finetune
model-index:
- name: wavlm-librispeech-clean-100h-dist
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wavlm-libri-clean-100h-large

This model is a fine-tuned version of [microsoft/wavlm-large](https://huggingface.co/microsoft/wavlm-large) on the LIBRISPEECH_ASR - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0601
- Wer: 0.0491

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
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- total_eval_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.8069        | 0.34  | 300  | 0.7510          | 0.5809 |
| 0.2483        | 0.67  | 600  | 0.2023          | 0.1929 |
| 0.1033        | 1.01  | 900  | 0.1123          | 0.1028 |
| 0.0742        | 1.35  | 1200 | 0.0858          | 0.0771 |
| 0.057         | 1.68  | 1500 | 0.0722          | 0.0663 |
| 0.0421        | 2.02  | 1800 | 0.0682          | 0.0582 |
| 0.0839        | 2.35  | 2100 | 0.0630          | 0.0534 |
| 0.0307        | 2.69  | 2400 | 0.0603          | 0.0508 |


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
