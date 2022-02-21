---
language:
- tr
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xlarge-...-common_voice-tr-demo
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xlarge-...-common_voice-tr-demo

This model is a fine-tuned version of [facebook/wav2vec2-xlarge-xlsr-...](https://huggingface.co/facebook/wav2vec2-xlarge-xlsr-...) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2701
- Wer: 0.2309
- Cer: 0.0527

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.00005
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 2
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- total_eval_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.4388        | 3.7   | 400  | 1.366          | 0.9701 |
| 0.3766        | 7.4   | 800  | 0.4914          | 0.5374 |
| 0.2295        | 11.11 | 1200 | 0.3934          | 0.4125 |
| 0.1121        | 14.81 | 1600 | 0.3264          | 0.2904 |
| 0.1473        | 18.51 | 2000 | 0.3103          | 0.2671 |
| 0.1013        | 22.22 | 2400 | 0.2589          | 0.2324 |
| 0.0704        | 25.92 | 2800 | 0.2826          | 0.2339 |
| 0.0537        | 29.63 | 3200 | 0.2704          | 0.2309 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
