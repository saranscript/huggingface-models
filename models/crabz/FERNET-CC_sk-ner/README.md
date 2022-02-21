---
license: cc-by-nc-sa-4.0
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
inference: false
model-index:
- name: fernet-sk-ner
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
      value: 0.9359821760118826
    - name: Recall
      type: recall
      value: 0.9472378804960541
    - name: F1
      type: f1
      value: 0.9415763914830033
    - name: Accuracy
      type: accuracy
      value: 0.9789063466534702
---

# Named Entity Recognition based on FERNET-CC_sk

This model is a fine-tuned version of [fav-kky/FERNET-CC_sk](https://huggingface.co/fav-kky/FERNET-CC_sk) on the Slovak wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1763
- Precision: 0.9360
- Recall: 0.9472
- F1: 0.9416
- Accuracy: 0.9789

## Intended uses & limitation
Supported classes: LOCATION, PERSON, ORGANIZATION

```
from transformers import pipeline

ner_pipeline = pipeline(task='ner', model='crabz/slovakbert-ner')
input_sentence = "Minister financií a líder mandátovo najsilnejšieho hnutia OĽaNO Igor Matovič upozorňuje, že následky tretej vlny budú na Slovensku veľmi veľké."
classifications = ner_pipeline(input_sentence)
``` 

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
| 0.1259        | 1.0   | 834  | 0.1095          | 0.8963    | 0.9182 | 0.9071 | 0.9697   |
| 0.071         | 2.0   | 1668 | 0.0974          | 0.9270    | 0.9357 | 0.9313 | 0.9762   |
| 0.0323        | 3.0   | 2502 | 0.1259          | 0.9257    | 0.9330 | 0.9293 | 0.9745   |
| 0.0175        | 4.0   | 3336 | 0.1347          | 0.9241    | 0.9360 | 0.9300 | 0.9756   |
| 0.0156        | 5.0   | 4170 | 0.1407          | 0.9337    | 0.9404 | 0.9370 | 0.9780   |
| 0.0062        | 6.0   | 5004 | 0.1522          | 0.9267    | 0.9410 | 0.9338 | 0.9774   |
| 0.0055        | 7.0   | 5838 | 0.1559          | 0.9322    | 0.9429 | 0.9375 | 0.9780   |
| 0.0024        | 8.0   | 6672 | 0.1733          | 0.9321    | 0.9438 | 0.9379 | 0.9779   |
| 0.0009        | 9.0   | 7506 | 0.1765          | 0.9347    | 0.9468 | 0.9407 | 0.9784   |
| 0.0002        | 10.0  | 8340 | 0.1763          | 0.9360    | 0.9472 | 0.9416 | 0.9789   |


### Framework versions

- Transformers 4.14.0.dev0
- Pytorch 1.10.0
- Datasets 1.16.1
- Tokenizers 0.10.3
