---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-common_voice-tr-ft-500sh
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-common_voice-tr-ft-500sh

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5794
- Wer: 0.4009
- Cer: 0.1032

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
| 0.5288        | 17.0   | 500  | 0.5099          | 0.5426 | 0.1432 |
| 0.2967        | 34.0   | 1000 | 0.5421          | 0.4746 | 0.1256 |
| 0.2447        | 51.0   | 1500 | 0.5347          | 0.4831 | 0.1267 |
| 0.122         | 68.01  | 2000 | 0.5854          | 0.4479 | 0.1161 |
| 0.1035        | 86.0   | 2500 | 0.5597          | 0.4457 | 0.1166 |
| 0.081         | 103.0  | 3000 | 0.5748          | 0.4250 | 0.1144 |
| 0.0849        | 120.0  | 3500 | 0.5598          | 0.4337 | 0.1145 |
| 0.0542        | 137.01 | 4000 | 0.5687          | 0.4223 | 0.1097 |
| 0.0318        | 155.0  | 4500 | 0.5904          | 0.4057 | 0.1052 |
| 0.0106        | 172.0  | 5000 | 0.5794          | 0.4009 | 0.1032 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.2
- Tokenizers 0.10.3
