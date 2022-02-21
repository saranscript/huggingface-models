---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
metrics:
- f1
model-index:
- name: text-to-sparql-t5-base-2021-10-19_15-35_lastDS
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metrics:
    - name: F1
      type: f1
      value: 0.3275993764400482
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# text-to-sparql-t5-base-2021-10-19_15-35_lastDS

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1310
- Gen Len: 19.0
- P: 0.5807
- R: 0.0962
- F1: 0.3276
- Score: 6.4533
- Bleu-precisions: [92.48113990507008, 85.38781447185119, 80.57856404313097, 77.37314727416516]
- Bleu-bp: 0.0770

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Gen Len | P      | R      | F1     | Score  | Bleu-precisions                                                              | Bleu-bp |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:------:|:------:|:------:|:----------------------------------------------------------------------------:|:-------:|
| nan           | 1.0   | 4807 | 0.1310          | 19.0    | 0.5807 | 0.0962 | 0.3276 | 6.4533 | [92.48113990507008, 85.38781447185119, 80.57856404313097, 77.37314727416516] | 0.0770  |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
