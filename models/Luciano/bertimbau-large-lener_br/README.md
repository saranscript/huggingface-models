---
license: mit
tags:
- generated_from_trainer
datasets:
- lener_br
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: bertimbau-large-lener_br
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: lener_br
      type: lener_br
      args: lener_br
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9801301293674859
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bertimbau-large-lener_br

This model is a fine-tuned version of [neuralmind/bert-large-portuguese-cased](https://huggingface.co/neuralmind/bert-large-portuguese-cased) on the lener_br dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1271
- Precision: 0.8965
- Recall: 0.9198
- F1: 0.9080
- Accuracy: 0.9801

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0674        | 1.0   | 1957  | 0.1349          | 0.7617    | 0.8710 | 0.8127 | 0.9594   |
| 0.0443        | 2.0   | 3914  | 0.1867          | 0.6862    | 0.9194 | 0.7858 | 0.9575   |
| 0.0283        | 3.0   | 5871  | 0.1185          | 0.8206    | 0.8766 | 0.8477 | 0.9678   |
| 0.0226        | 4.0   | 7828  | 0.1405          | 0.8072    | 0.8978 | 0.8501 | 0.9708   |
| 0.0141        | 5.0   | 9785  | 0.1898          | 0.7224    | 0.9194 | 0.8090 | 0.9629   |
| 0.01          | 6.0   | 11742 | 0.1655          | 0.9062    | 0.8856 | 0.8958 | 0.9741   |
| 0.012         | 7.0   | 13699 | 0.1271          | 0.8965    | 0.9198 | 0.9080 | 0.9801   |
| 0.0091        | 8.0   | 15656 | 0.1919          | 0.8890    | 0.8886 | 0.8888 | 0.9719   |
| 0.0042        | 9.0   | 17613 | 0.1725          | 0.8977    | 0.8985 | 0.8981 | 0.9744   |
| 0.0043        | 10.0  | 19570 | 0.1530          | 0.8878    | 0.9034 | 0.8955 | 0.9761   |
| 0.0042        | 11.0  | 21527 | 0.1635          | 0.8792    | 0.9108 | 0.8947 | 0.9774   |
| 0.0033        | 12.0  | 23484 | 0.2009          | 0.8155    | 0.9138 | 0.8619 | 0.9719   |
| 0.0008        | 13.0  | 25441 | 0.1766          | 0.8737    | 0.9135 | 0.8932 | 0.9755   |
| 0.0005        | 14.0  | 27398 | 0.1868          | 0.8616    | 0.9129 | 0.8865 | 0.9743   |
| 0.0014        | 15.0  | 29355 | 0.1910          | 0.8694    | 0.9101 | 0.8893 | 0.9746   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.9.0+cu102
- Datasets 1.9.0
- Tokenizers 0.10.3
