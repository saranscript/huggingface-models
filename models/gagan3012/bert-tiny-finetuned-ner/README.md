---
tags:
- generated_from_trainer
datasets:
- conll2003
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: bert-tiny-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metrics:
    - name: Precision
      type: precision
      value: 0.8083060109289617
    - name: Recall
      type: recall
      value: 0.8273856136033113
    - name: F1
      type: f1
      value: 0.8177345348001547
    - name: Accuracy
      type: accuracy
      value: 0.9597597979252387
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-tiny-finetuned-ner

This model is a fine-tuned version of [prajjwal1/bert-tiny](https://huggingface.co/prajjwal1/bert-tiny) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1689
- Precision: 0.8083
- Recall: 0.8274
- F1: 0.8177
- Accuracy: 0.9598

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0355        | 1.0   | 878  | 0.1692          | 0.8072    | 0.8248 | 0.8159 | 0.9594   |
| 0.0411        | 2.0   | 1756 | 0.1678          | 0.8101    | 0.8277 | 0.8188 | 0.9600   |
| 0.0386        | 3.0   | 2634 | 0.1697          | 0.8103    | 0.8269 | 0.8186 | 0.9599   |
| 0.0373        | 4.0   | 3512 | 0.1694          | 0.8106    | 0.8263 | 0.8183 | 0.9600   |
| 0.0383        | 5.0   | 4390 | 0.1689          | 0.8083    | 0.8274 | 0.8177 | 0.9598   |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
