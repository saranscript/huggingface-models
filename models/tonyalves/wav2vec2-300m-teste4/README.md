---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-300m-teste4
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-300m-teste4

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3276
- Wer: 0.3489

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 4
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 10.0237       | 0.49  | 100  | 4.2075          | 0.9792 |
| 3.313         | 0.98  | 200  | 3.0232          | 0.9792 |
| 2.9469        | 1.47  | 300  | 2.7591          | 0.9792 |
| 1.4217        | 1.96  | 400  | 0.8397          | 0.6219 |
| 0.5598        | 2.45  | 500  | 0.6085          | 0.5087 |
| 0.4507        | 2.94  | 600  | 0.4512          | 0.4317 |
| 0.2775        | 3.43  | 700  | 0.3839          | 0.3751 |
| 0.2047        | 3.92  | 800  | 0.3276          | 0.3489 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1+cu102
- Datasets 1.17.0
- Tokenizers 0.10.3
