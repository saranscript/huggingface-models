---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: mbarthez-copy_mechanism-hal_articles
  results:
  - task:
      name: Summarization
      type: summarization
    metrics:
    - name: Rouge1
      type: rouge
      value: 36.548
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mbarthez-davide_articles-copy_enhanced

This model is a fine-tuned version of [moussaKam/mbarthez](https://huggingface.co/moussaKam/mbarthez) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4905
- Rouge1: 36.548
- Rouge2: 19.6282
- Rougel: 30.2513
- Rougelsum: 30.2765
- Gen Len: 25.7238

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| 1.6706        | 1.0   | 33552  | 1.5690          | 31.2477 | 16.5455 | 26.9855 | 26.9754   | 18.6217 |
| 1.3446        | 2.0   | 67104  | 1.5060          | 32.1108 | 17.1408 | 27.7833 | 27.7703   | 18.9115 |
| 1.3245        | 3.0   | 100656 | 1.4905          | 32.9084 | 17.7027 | 28.2912 | 28.2975   | 18.9801 |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1+cu110
- Datasets 1.11.0
- Tokenizers 0.10.3
