---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: byt5-base-finetuned-modernisa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# byt5-base-finetuned-modernisa

This model is a fine-tuned version of [google/byt5-base](https://huggingface.co/google/byt5-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1176
- Bleu: 44.888
- Gen Len: 18.4465

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 0.1474        | 0.35  | 10000 | 0.1360          | 42.8789 | 18.4441 |
| 0.1328        | 0.71  | 20000 | 0.1303          | 43.5394 | 18.4368 |
| 0.1216        | 1.06  | 30000 | 0.1245          | 44.1557 | 18.4384 |
| 0.1167        | 1.42  | 40000 | 0.1219          | 44.1961 | 18.4449 |
| 0.1065        | 1.77  | 50000 | 0.1192          | 44.7353 | 18.443  |
| 0.099         | 2.13  | 60000 | 0.1195          | 44.522  | 18.4524 |
| 0.088         | 2.48  | 70000 | 0.1192          | 44.8243 | 18.4441 |
| 0.0907        | 2.84  | 80000 | 0.1176          | 44.888  | 18.4465 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
