---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
model_index:
- name: distilgpt2-finetuned-distilgpt2-med_articles
  results:
  - task:
      name: Causal Language Modeling
      type: text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilgpt2-finetuned-distilgpt2-med_articles

This model is a fine-tuned version of [vishnun/distilgpt2-finetuned-distilgpt2-med_articles](https://huggingface.co/vishnun/distilgpt2-finetuned-distilgpt2-med_articles) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.3171

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 65   | 3.3417          |
| No log        | 2.0   | 130  | 3.3300          |
| No log        | 3.0   | 195  | 3.3231          |
| No log        | 4.0   | 260  | 3.3172          |
| No log        | 5.0   | 325  | 3.3171          |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
