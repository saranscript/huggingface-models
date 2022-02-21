---
tags:
- automatic-speech-recognition
- librispeech_asr
- generated_from_trainer
- wavlm_libri_finetune
model-index:
- name: wavlm-libri-clean-100h-base
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wavlm-libri-clean-100h-base

This model is a fine-tuned version of [microsoft/wavlm-base](https://huggingface.co/microsoft/wavlm-base) on the LIBRISPEECH_ASR - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0829
- Wer: 0.0675

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
- eval_batch_size: 4
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 32
- total_eval_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.8805        | 0.34  | 300  | 2.8686          | 1.0    |
| 0.2459        | 0.67  | 600  | 0.1858          | 0.1554 |
| 0.1114        | 1.01  | 900  | 0.1379          | 0.1191 |
| 0.0867        | 1.35  | 1200 | 0.1130          | 0.0961 |
| 0.0698        | 1.68  | 1500 | 0.1032          | 0.0877 |
| 0.0663        | 2.02  | 1800 | 0.0959          | 0.0785 |
| 0.0451        | 2.35  | 2100 | 0.0887          | 0.0748 |
| 0.0392        | 2.69  | 2400 | 0.0859          | 0.0698 |


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
