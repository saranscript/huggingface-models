---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-en-mul-finetuned-en-to-th_test
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-en-mul-finetuned-en-to-th_test

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-mul](https://huggingface.co/Helsinki-NLP/opus-mt-en-mul) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1433
- Bleu: 87.489
- Gen Len: 41.8746

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0002
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 0.3015        | 1.0   | 1644  | 0.2647          | 74.0346 | 40.8573 |
| 0.2375        | 2.0   | 3288  | 0.2063          | 77.7781 | 41.5813 |
| 0.1843        | 3.0   | 4932  | 0.1790          | 79.4476 | 41.6881 |
| 0.1203        | 4.0   | 6576  | 0.1638          | 80.2861 | 41.454  |
| 0.0951        | 5.0   | 8220  | 0.1502          | 82.7682 | 41.6016 |
| 0.0836        | 6.0   | 9864  | 0.1454          | 83.9187 | 41.7407 |
| 0.0471        | 7.0   | 11508 | 0.1429          | 84.9791 | 41.836  |
| 0.039         | 8.0   | 13152 | 0.1415          | 85.995  | 41.8348 |
| 0.024         | 9.0   | 14796 | 0.1418          | 86.9521 | 41.923  |
| 0.0129        | 10.0  | 16440 | 0.1433          | 87.489  | 41.8746 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
