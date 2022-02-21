---
tags:
- generated_from_trainer
datasets:
- wikiann
metrics:
- precision
- recall
- f1
- accuracy
language:
- sk
model-index:
- name: bertoslav-limited-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann sk
      type: wikiann
      args: sk
    metrics:
    - name: Precision
      type: precision
      value: 0.8985571260306242
    - name: Recall
      type: recall
      value: 0.9173994738819993
    - name: F1
      type: f1
      value: 0.9078805459481573
    - name: Accuracy
      type: accuracy
      value: 0.9700235061239639
---

# Named Entity Recognition based on bertoslav-limited

This model is a fine-tuned version of [crabz/bertoslav-limited](https://huggingface.co/crabz/bertoslav-limited) on the Slovak wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2119
- Precision: 0.8986
- Recall: 0.9174
- F1: 0.9079
- Accuracy: 0.9700

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 24
- eval_batch_size: 24
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2953        | 1.0   | 834  | 0.1516          | 0.8413    | 0.8647 | 0.8529 | 0.9549   |
| 0.0975        | 2.0   | 1668 | 0.1304          | 0.8787    | 0.9056 | 0.8920 | 0.9658   |
| 0.0487        | 3.0   | 2502 | 0.1405          | 0.8916    | 0.8958 | 0.8937 | 0.9660   |
| 0.025         | 4.0   | 3336 | 0.1658          | 0.8850    | 0.9116 | 0.8981 | 0.9669   |
| 0.0161        | 5.0   | 4170 | 0.1739          | 0.8974    | 0.9127 | 0.9050 | 0.9693   |
| 0.0074        | 6.0   | 5004 | 0.1888          | 0.8900    | 0.9144 | 0.9020 | 0.9687   |
| 0.0051        | 7.0   | 5838 | 0.1996          | 0.8946    | 0.9145 | 0.9044 | 0.9693   |
| 0.0039        | 8.0   | 6672 | 0.2052          | 0.8993    | 0.9158 | 0.9075 | 0.9697   |
| 0.0024        | 9.0   | 7506 | 0.2112          | 0.8946    | 0.9171 | 0.9057 | 0.9696   |
| 0.0018        | 10.0  | 8340 | 0.2119          | 0.8986    | 0.9174 | 0.9079 | 0.9700   |


### Framework versions

- Transformers 4.14.0.dev0
- Pytorch 1.10.0
- Datasets 1.16.1
- Tokenizers 0.10.3
