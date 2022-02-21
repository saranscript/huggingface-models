---
license: mit
tags:
- generated_from_trainer
datasets:
- conll2003
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: xlm-roberta-base-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9882987313361343
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-base-finetuned-ner

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1202
- Precision: 0.9447
- Recall: 0.9536
- F1: 0.9492
- Accuracy: 0.9883

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
- train_batch_size: 5
- eval_batch_size: 5
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 30

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.1023        | 1.0   | 2809  | 0.0724          | 0.9338    | 0.9363 | 0.9351 | 0.9850   |
| 0.0596        | 2.0   | 5618  | 0.0760          | 0.9295    | 0.9359 | 0.9327 | 0.9848   |
| 0.0406        | 3.0   | 8427  | 0.0740          | 0.9346    | 0.9410 | 0.9378 | 0.9863   |
| 0.0365        | 4.0   | 11236 | 0.0676          | 0.9368    | 0.9490 | 0.9428 | 0.9870   |
| 0.0279        | 5.0   | 14045 | 0.0737          | 0.9453    | 0.9476 | 0.9464 | 0.9877   |
| 0.0147        | 6.0   | 16854 | 0.0812          | 0.9413    | 0.9515 | 0.9464 | 0.9878   |
| 0.0138        | 7.0   | 19663 | 0.0893          | 0.9425    | 0.9525 | 0.9475 | 0.9876   |
| 0.0158        | 8.0   | 22472 | 0.1066          | 0.9362    | 0.9464 | 0.9412 | 0.9862   |
| 0.0092        | 9.0   | 25281 | 0.1026          | 0.9391    | 0.9511 | 0.9451 | 0.9869   |
| 0.0073        | 10.0  | 28090 | 0.1001          | 0.9442    | 0.9503 | 0.9472 | 0.9879   |
| 0.0069        | 11.0  | 30899 | 0.1103          | 0.9399    | 0.9511 | 0.9455 | 0.9871   |
| 0.0073        | 12.0  | 33708 | 0.1170          | 0.9383    | 0.9481 | 0.9432 | 0.9876   |
| 0.0054        | 13.0  | 36517 | 0.1068          | 0.9407    | 0.9491 | 0.9448 | 0.9875   |
| 0.0048        | 14.0  | 39326 | 0.1096          | 0.9438    | 0.9518 | 0.9477 | 0.9879   |
| 0.0042        | 15.0  | 42135 | 0.1187          | 0.9442    | 0.9523 | 0.9483 | 0.9884   |
| 0.0037        | 16.0  | 44944 | 0.1162          | 0.9384    | 0.9521 | 0.9452 | 0.9875   |
| 0.0039        | 17.0  | 47753 | 0.1046          | 0.9435    | 0.9477 | 0.9456 | 0.9878   |
| 0.0025        | 18.0  | 50562 | 0.1063          | 0.9501    | 0.9549 | 0.9525 | 0.9889   |
| 0.0021        | 19.0  | 53371 | 0.0992          | 0.9533    | 0.9572 | 0.9553 | 0.9895   |
| 0.0019        | 20.0  | 56180 | 0.1216          | 0.9404    | 0.9524 | 0.9464 | 0.9876   |
| 0.0021        | 21.0  | 58989 | 0.1080          | 0.9430    | 0.9478 | 0.9454 | 0.9880   |
| 0.0032        | 22.0  | 61798 | 0.1109          | 0.9436    | 0.9512 | 0.9474 | 0.9881   |
| 0.0115        | 23.0  | 64607 | 0.1161          | 0.9412    | 0.9475 | 0.9443 | 0.9874   |
| 0.001         | 24.0  | 67416 | 0.1216          | 0.9446    | 0.9518 | 0.9481 | 0.9882   |
| 0.0004        | 25.0  | 70225 | 0.1145          | 0.9478    | 0.9527 | 0.9503 | 0.9888   |
| 0.0005        | 26.0  | 73034 | 0.1217          | 0.9479    | 0.9531 | 0.9505 | 0.9887   |
| 0.0007        | 27.0  | 75843 | 0.1199          | 0.9452    | 0.9561 | 0.9506 | 0.9887   |
| 0.0053        | 28.0  | 78652 | 0.1187          | 0.9440    | 0.9510 | 0.9475 | 0.9881   |
| 0.0014        | 29.0  | 81461 | 0.1207          | 0.9461    | 0.9540 | 0.9500 | 0.9884   |
| 0.0023        | 30.0  | 84270 | 0.1202          | 0.9447    | 0.9536 | 0.9492 | 0.9883   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
