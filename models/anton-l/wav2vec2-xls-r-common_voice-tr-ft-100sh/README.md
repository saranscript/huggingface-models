---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-common_voice-tr-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-common_voice-tr-ft

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5806
- Wer: 0.3998
- Cer: 0.1053

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
- num_devices: 4
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- total_eval_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- training_steps: 5000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:------:|:----:|:---------------:|:------:|:------:|
| 0.5369        | 17.0   | 500  | 0.6021          | 0.6366 | 0.1727 |
| 0.3542        | 34.0   | 1000 | 0.5265          | 0.4906 | 0.1278 |
| 0.1866        | 51.0   | 1500 | 0.5805          | 0.4768 | 0.1261 |
| 0.1674        | 68.01  | 2000 | 0.5336          | 0.4518 | 0.1186 |
| 0.19          | 86.0   | 2500 | 0.5676          | 0.4427 | 0.1151 |
| 0.0815        | 103.0  | 3000 | 0.5510          | 0.4268 | 0.1125 |
| 0.0545        | 120.0  | 3500 | 0.5608          | 0.4175 | 0.1099 |
| 0.0299        | 137.01 | 4000 | 0.5875          | 0.4222 | 0.1124 |
| 0.0267        | 155.0  | 4500 | 0.5882          | 0.4026 | 0.1063 |
| 0.025         | 172.0  | 5000 | 0.5806          | 0.3998 | 0.1053 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.2
- Tokenizers 0.10.3
