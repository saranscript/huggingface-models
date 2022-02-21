---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- squad
model_index:
- name: bert-base-uncased-finetuned-squad
  results:
  - task:
      name: Question Answering
      type: question-answering
    dataset:
      name: squad
      type: squad
      args: plain_text
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-squad

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the SQuAD1.1 dataset. It was trained through Transformers' example Colab notebook on Question Answering, available [here](https://colab.research.google.com/github/huggingface/notebooks/blob/master/examples/question_answering.ipynb).
It achieves the following results on the evaluation set:
- Loss: 1.0780

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training. They are equal to the ones used to fine-tune [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) for QA:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.0706        | 1.0   | 5533  | 1.0250          |
| 0.7899        | 2.0   | 11066 | 1.0356          |
| 0.5991        | 3.0   | 16599 | 1.0780          |


### Validation results

|    EM    |   F1    |
|:--------:|:-------:|
| 80.3690  | 88.0110 |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
