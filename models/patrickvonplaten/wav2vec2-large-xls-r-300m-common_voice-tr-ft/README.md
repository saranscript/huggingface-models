---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- xls_r_repro_common_voice_tr
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-common_voice-tr-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-common_voice-tr-ft

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4179
- Wer: 0.3071
- Cer: 0.0736

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 64
- total_eval_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 0.7638        | 9.09  | 500  | 0.4763          | 0.5313 | 0.1333 |
| 0.5739        | 18.18 | 1000 | 0.4007          | 0.4357 | 0.1099 |
| 0.4343        | 27.27 | 1500 | 0.3819          | 0.4060 | 0.1012 |
| 0.4401        | 36.36 | 2000 | 0.3991          | 0.3954 | 0.1001 |
| 0.2647        | 45.45 | 2500 | 0.3901          | 0.3689 | 0.0914 |
| 0.2656        | 54.55 | 3000 | 0.4284          | 0.3463 | 0.0852 |
| 0.2586        | 63.64 | 3500 | 0.4084          | 0.3297 | 0.0804 |
| 0.2041        | 72.73 | 4000 | 0.3907          | 0.3193 | 0.0781 |
| 0.4265        | 81.82 | 4500 | 0.4265          | 0.3120 | 0.0755 |
| 0.2041        | 90.91 | 5000 | 0.4240          | 0.3071 | 0.0736 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
