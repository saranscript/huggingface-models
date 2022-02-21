---
license: mit
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
- precision
- recall
model-index:
- name: deberta-v3-base-ptc
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# deberta-v3-base-ptc

This model is a fine-tuned version of [microsoft/deberta-v3-base](https://huggingface.co/microsoft/deberta-v3-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0174
- Accuracy: 0.9945
- F1: 0.9885
- Precision: 0.9864
- Recall: 0.9906

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
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 32
- total_train_batch_size: 512
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.01
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Precision | Recall |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:---------:|:------:|
| 0.0834        | 0.1   | 300  | 0.0815          | 0.9733   | 0.9365 | 0.9256    | 0.9498 |
| 0.0853        | 0.2   | 600  | 0.0600          | 0.9817   | 0.9576 | 0.9525    | 0.9637 |
| 0.0427        | 0.29  | 900  | 0.0386          | 0.9874   | 0.9701 | 0.9661    | 0.9747 |
| 0.0427        | 0.39  | 1200 | 0.0408          | 0.9888   | 0.9746 | 0.9763    | 0.9730 |
| 0.0432        | 0.49  | 1500 | 0.0311          | 0.9896   | 0.9761 | 0.9770    | 0.9756 |
| 0.0314        | 0.59  | 1800 | 0.0305          | 0.9899   | 0.9794 | 0.9767    | 0.9824 |
| 0.0167        | 0.69  | 2100 | 0.0236          | 0.9925   | 0.9820 | 0.9793    | 0.9851 |
| 0.0243        | 0.78  | 2400 | 0.0206          | 0.9934   | 0.9852 | 0.9838    | 0.9866 |
| 0.0228        | 0.88  | 2700 | 0.0183          | 0.9941   | 0.9859 | 0.9822    | 0.9898 |
| 0.009         | 0.98  | 3000 | 0.0170          | 0.9945   | 0.9879 | 0.9862    | 0.9896 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.8.1+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
