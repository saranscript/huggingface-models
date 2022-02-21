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
      value: 0.90090188725725
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-base-finetuned-ner

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4181
- Precision: 0.6464
- Recall: 0.4904
- F1: 0.5577
- Accuracy: 0.9009
- It just needs more training time

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
| 0.9474        | 1.0   | 2809  | 0.9105          | 0.0       | 0.0    | 0.0    | 0.7879   |
| 0.7728        | 2.0   | 5618  | 0.8002          | 0.0       | 0.0    | 0.0    | 0.7879   |
| 0.7209        | 3.0   | 8427  | 0.7329          | 0.1818    | 0.0002 | 0.0004 | 0.7881   |
| 0.6666        | 4.0   | 11236 | 0.6824          | 0.27      | 0.0050 | 0.0099 | 0.7903   |
| 0.6372        | 5.0   | 14045 | 0.6416          | 0.3302    | 0.0261 | 0.0484 | 0.7988   |
| 0.5982        | 6.0   | 16854 | 0.6084          | 0.4188    | 0.0686 | 0.1179 | 0.8128   |
| 0.5812        | 7.0   | 19663 | 0.5800          | 0.4799    | 0.1152 | 0.1858 | 0.8266   |
| 0.5684        | 8.0   | 22472 | 0.5569          | 0.5255    | 0.1647 | 0.2508 | 0.8380   |
| 0.5389        | 9.0   | 25281 | 0.5375          | 0.5564    | 0.2128 | 0.3078 | 0.8482   |
| 0.5307        | 10.0  | 28090 | 0.5205          | 0.5749    | 0.2550 | 0.3533 | 0.8567   |
| 0.5106        | 11.0  | 30899 | 0.5064          | 0.5916    | 0.2916 | 0.3906 | 0.8636   |
| 0.4921        | 12.0  | 33708 | 0.4938          | 0.6033    | 0.3236 | 0.4212 | 0.8698   |
| 0.4967        | 13.0  | 36517 | 0.4825          | 0.6106    | 0.3544 | 0.4485 | 0.8758   |
| 0.4707        | 14.0  | 39326 | 0.4733          | 0.6199    | 0.3753 | 0.4676 | 0.8798   |
| 0.4704        | 15.0  | 42135 | 0.4654          | 0.6246    | 0.3927 | 0.4823 | 0.8830   |
| 0.4654        | 16.0  | 44944 | 0.4574          | 0.6285    | 0.4159 | 0.5006 | 0.8871   |
| 0.4314        | 17.0  | 47753 | 0.4514          | 0.6321    | 0.4240 | 0.5075 | 0.8887   |
| 0.47          | 18.0  | 50562 | 0.4459          | 0.6358    | 0.4380 | 0.5187 | 0.8911   |
| 0.4486        | 19.0  | 53371 | 0.4410          | 0.6399    | 0.4480 | 0.5271 | 0.8929   |
| 0.4411        | 20.0  | 56180 | 0.4367          | 0.6413    | 0.4561 | 0.5331 | 0.8944   |
| 0.4333        | 21.0  | 58989 | 0.4328          | 0.6411    | 0.4644 | 0.5386 | 0.8959   |
| 0.4402        | 22.0  | 61798 | 0.4295          | 0.6425    | 0.4687 | 0.5420 | 0.8968   |
| 0.4287        | 23.0  | 64607 | 0.4268          | 0.6442    | 0.4735 | 0.5458 | 0.8978   |
| 0.4336        | 24.0  | 67416 | 0.4245          | 0.6441    | 0.4771 | 0.5482 | 0.8985   |
| 0.4243        | 25.0  | 70225 | 0.4224          | 0.6454    | 0.4817 | 0.5517 | 0.8993   |
| 0.4153        | 26.0  | 73034 | 0.4209          | 0.6469    | 0.4846 | 0.5541 | 0.8998   |
| 0.4286        | 27.0  | 75843 | 0.4197          | 0.6467    | 0.4865 | 0.5553 | 0.9002   |
| 0.436         | 28.0  | 78652 | 0.4188          | 0.6466    | 0.4887 | 0.5566 | 0.9006   |
| 0.427         | 29.0  | 81461 | 0.4183          | 0.6465    | 0.4900 | 0.5575 | 0.9008   |
| 0.4317        | 30.0  | 84270 | 0.4181          | 0.6464    | 0.4904 | 0.5577 | 0.9009   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
