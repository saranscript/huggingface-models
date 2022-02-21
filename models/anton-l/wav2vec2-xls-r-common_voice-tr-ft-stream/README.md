---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-common_voice-tr-ft-stream
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-common_voice-tr-ft-stream

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3519
- Wer: 0.2927
- Cer: 0.0694

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

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 0.6768        | 9.01  | 500  | 0.4220          | 0.5143 | 0.1235 |
| 0.3801        | 19.01 | 1000 | 0.3303          | 0.4403 | 0.1055 |
| 0.3616        | 29.0  | 1500 | 0.3540          | 0.3716 | 0.0878 |
| 0.2334        | 39.0  | 2000 | 0.3666          | 0.3671 | 0.0842 |
| 0.3141        | 49.0  | 2500 | 0.3407          | 0.3373 | 0.0819 |
| 0.1926        | 58.01 | 3000 | 0.3886          | 0.3520 | 0.0867 |
| 0.1372        | 68.01 | 3500 | 0.3415          | 0.3189 | 0.0743 |
| 0.091         | 78.0  | 4000 | 0.3750          | 0.3164 | 0.0757 |
| 0.0893        | 88.0  | 4500 | 0.3559          | 0.2968 | 0.0712 |
| 0.095         | 98.0  | 5000 | 0.3519          | 0.2927 | 0.0694 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.2
- Tokenizers 0.10.3
