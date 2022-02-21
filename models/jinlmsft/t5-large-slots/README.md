---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: t5-large-slots
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-large-slots

This model is a fine-tuned version of [t5-large](https://huggingface.co/t5-large) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0889
- Acc: 0.76
- True Num: 11167
- Num: 14748

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 16
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Acc  | True Num | Num   |
|:-------------:|:-----:|:-----:|:---------------:|:----:|:--------:|:-----:|
| 0.3539        | 0.56  | 1000  | 0.2669          | 0.56 | 8264     | 14748 |
| 0.2523        | 1.13  | 2000  | 0.2031          | 0.56 | 8317     | 14748 |
| 0.2003        | 1.69  | 3000  | 0.1498          | 0.58 | 8496     | 14748 |
| 0.1609        | 2.25  | 4000  | 0.1284          | 0.58 | 8612     | 14748 |
| 0.1431        | 2.82  | 5000  | 0.1119          | 0.59 | 8675     | 14748 |
| 0.1236        | 3.38  | 6000  | 0.1054          | 0.59 | 8737     | 14748 |
| 0.1172        | 3.95  | 7000  | 0.0981          | 0.59 | 8773     | 14748 |
| 0.1027        | 4.51  | 8000  | 0.0955          | 0.6  | 8787     | 14748 |
| 0.0968        | 5.07  | 9000  | 0.0931          | 0.6  | 8807     | 14748 |
| 0.0911        | 5.64  | 10000 | 0.0895          | 0.6  | 8787     | 14748 |
| 0.0852        | 6.2   | 11000 | 0.0912          | 0.6  | 8840     | 14748 |
| 0.0823        | 6.76  | 12000 | 0.0880          | 0.6  | 8846     | 14748 |
| 0.0768        | 7.33  | 13000 | 0.0915          | 0.6  | 8879     | 14748 |
| 0.0758        | 7.89  | 14000 | 0.0892          | 0.6  | 8853     | 14748 |
| 0.0708        | 8.46  | 15000 | 0.0885          | 0.6  | 8884     | 14748 |
| 0.0701        | 9.02  | 16000 | 0.0884          | 0.6  | 8915     | 14748 |
| 0.0685        | 9.58  | 17000 | 0.0884          | 0.6  | 8921     | 14748 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
