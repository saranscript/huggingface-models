---
tags:
- generated_from_trainer
model-index:
- name: ViTGPT2_VW
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ViTGPT2_VW

This model is a fine-tuned version of [](https://huggingface.co/) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0771

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- distributed_type: multi-GPU
- num_devices: 2
- total_train_batch_size: 4
- total_eval_batch_size: 4
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 0.1256        | 0.03  | 1000  | 0.0928          |
| 0.0947        | 0.07  | 2000  | 0.0897          |
| 0.0889        | 0.1   | 3000  | 0.0859          |
| 0.0888        | 0.14  | 4000  | 0.0842          |
| 0.0866        | 0.17  | 5000  | 0.0831          |
| 0.0852        | 0.2   | 6000  | 0.0819          |
| 0.0833        | 0.24  | 7000  | 0.0810          |
| 0.0835        | 0.27  | 8000  | 0.0802          |
| 0.081         | 0.31  | 9000  | 0.0796          |
| 0.0803        | 0.34  | 10000 | 0.0789          |
| 0.0814        | 0.38  | 11000 | 0.0785          |
| 0.0799        | 0.41  | 12000 | 0.0780          |
| 0.0786        | 0.44  | 13000 | 0.0776          |
| 0.0796        | 0.48  | 14000 | 0.0771          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0
