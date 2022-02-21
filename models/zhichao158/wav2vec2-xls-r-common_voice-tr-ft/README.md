---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-common_voice-tr-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-common_voice-tr-ft

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3736
- Wer: 0.2930
- Cer: 0.0708

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
- train_batch_size: 12
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 96
- total_eval_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 0.5462        | 13.51 | 500  | 0.4423          | 0.4807 | 0.1188 |
| 0.342         | 27.03 | 1000 | 0.3781          | 0.3954 | 0.0967 |
| 0.2272        | 40.54 | 1500 | 0.3816          | 0.3595 | 0.0893 |
| 0.1805        | 54.05 | 2000 | 0.3943          | 0.3487 | 0.0854 |
| 0.1318        | 67.57 | 2500 | 0.3818          | 0.3262 | 0.0801 |
| 0.1213        | 81.08 | 3000 | 0.3777          | 0.3113 | 0.0758 |
| 0.0639        | 94.59 | 3500 | 0.3788          | 0.2953 | 0.0716 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.8.0
- Datasets 1.17.0
- Tokenizers 0.10.3
