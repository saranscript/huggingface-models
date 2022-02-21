---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
model_index:
- name: distilgpt2-finetuned-tamilmixsentiment
  results:
  - task:
      name: Causal Language Modeling
      type: text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilgpt2-finetuned-tamilmixsentiment

This model is a fine-tuned version of [distilgpt2](https://huggingface.co/distilgpt2) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 4.4572

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
| 5.6438        | 1.0   | 907  | 4.8026          |
| 4.774         | 2.0   | 1814 | 4.5953          |
| 4.5745        | 3.0   | 2721 | 4.5070          |
| 4.4677        | 4.0   | 3628 | 4.4688          |
| 4.4294        | 5.0   | 4535 | 4.4572          |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
