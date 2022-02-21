---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-base-uncased-finetuned-infovqa
  results:
  - task:
      name: Question Answering
      type: question-answering
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-infovqa

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.8276

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
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 3.2765        | 0.23  | 1000 | 3.0678          |
| 2.9987        | 0.46  | 2000 | 2.9525          |
| 2.826         | 0.69  | 3000 | 2.7870          |
| 2.7084        | 0.93  | 4000 | 2.7051          |
| 2.1286        | 1.16  | 5000 | 2.9286          |
| 2.0009        | 1.39  | 6000 | 3.1037          |
| 2.0323        | 1.62  | 7000 | 2.8567          |
| 1.9905        | 1.85  | 8000 | 2.8276          |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.8.0+cu101
- Datasets 1.11.0
- Tokenizers 0.10.3
