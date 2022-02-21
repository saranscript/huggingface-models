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
- name: bertimbau-base-lener_br
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
      value: 0.9692504609383333
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bertimbau-base-lener_br

This model is a fine-tuned version of [neuralmind/bert-base-portuguese-cased](https://huggingface.co/neuralmind/bert-base-portuguese-cased) on the lener_br dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2298
- Precision: 0.8501
- Recall: 0.9138
- F1: 0.8808
- Accuracy: 0.9693

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
| 0.0686        | 1.0   | 1957  | 0.1399          | 0.7759    | 0.8669 | 0.8189 | 0.9641   |
| 0.0437        | 2.0   | 3914  | 0.1457          | 0.7997    | 0.8938 | 0.8441 | 0.9623   |
| 0.0313        | 3.0   | 5871  | 0.1675          | 0.8466    | 0.8744 | 0.8603 | 0.9651   |
| 0.0201        | 4.0   | 7828  | 0.1621          | 0.8713    | 0.8839 | 0.8775 | 0.9718   |
| 0.0137        | 5.0   | 9785  | 0.1811          | 0.7783    | 0.9159 | 0.8415 | 0.9645   |
| 0.0105        | 6.0   | 11742 | 0.1836          | 0.8568    | 0.9009 | 0.8783 | 0.9692   |
| 0.0105        | 7.0   | 13699 | 0.1649          | 0.8339    | 0.9125 | 0.8714 | 0.9725   |
| 0.0059        | 8.0   | 15656 | 0.2298          | 0.8501    | 0.9138 | 0.8808 | 0.9693   |
| 0.0051        | 9.0   | 17613 | 0.2210          | 0.8437    | 0.9045 | 0.8731 | 0.9693   |
| 0.0061        | 10.0  | 19570 | 0.2499          | 0.8627    | 0.8946 | 0.8784 | 0.9681   |
| 0.0041        | 11.0  | 21527 | 0.1985          | 0.8560    | 0.9052 | 0.8799 | 0.9720   |
| 0.003         | 12.0  | 23484 | 0.2204          | 0.8498    | 0.9065 | 0.8772 | 0.9699   |
| 0.0014        | 13.0  | 25441 | 0.2152          | 0.8425    | 0.9067 | 0.8734 | 0.9709   |
| 0.0005        | 14.0  | 27398 | 0.2317          | 0.8553    | 0.8987 | 0.8765 | 0.9705   |
| 0.0015        | 15.0  | 29355 | 0.2436          | 0.8543    | 0.8989 | 0.8760 | 0.9700   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.9.0+cu102
- Datasets 1.9.0
- Tokenizers 0.10.3
