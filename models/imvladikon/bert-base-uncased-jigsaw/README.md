---
language:
- en
license: 
tags:
- generated_from_trainer
datasets:
- jigsaw
model_index:
- name: bert-base-uncased
  results:
  - {}
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased

This model is a fine-tuned version of [](https://huggingface.co/) on the jigsaw dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0393
- Precision Micro: 0.7758
- Recall Micro: 0.7858
- F1 Micro: 0.7808
- F2 Micro: 0.7838
- Precision Macro: 0.6349
- Recall Macro: 0.5972
- F1 Macro: 0.6105
- F2 Macro: 0.6015
- Overall Precision: 0.9841
- Overall Recall: 0.9841
- Overall F1: 0.9841
- Overall F2: 0.9841
- Overall Accuracy: 0.9841
- Matthews Corrcoef: 0.7725
- Aucroc Macro: 0.9897
- Aucroc Micro: 0.9920
- Accuracy Toxic: 0.9678
- F1 Toxic: 0.8295
- Accuracy Severe Toxic: 0.9899
- F1 Severe Toxic: 0.3313
- Accuracy Obscene: 0.9816
- F1 Obscene: 0.8338
- Accuracy Threat: 0.9974
- F1 Threat: 0.4545
- Accuracy Insult: 0.9763
- F1 Insult: 0.7662
- Accuracy Identity Hate: 0.9914
- F1 Identity Hate: 0.4480

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 24
- eval_batch_size: 12
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 48
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision Micro | Recall Micro | F1 Micro | F2 Micro | Precision Macro | Recall Macro | F1 Macro | F2 Macro | Overall Precision | Overall Recall | Overall F1 | Overall F2 | Overall Accuracy | Matthews Corrcoef | Aucroc Macro | Aucroc Micro | Accuracy Toxic | F1 Toxic | Accuracy Severe Toxic | F1 Severe Toxic | Accuracy Obscene | F1 Obscene | Accuracy Threat | F1 Threat | Accuracy Insult | F1 Insult | Accuracy Identity Hate | F1 Identity Hate |
|:-------------:|:-----:|:-----:|:---------------:|:---------------:|:------------:|:--------:|:--------:|:---------------:|:------------:|:--------:|:--------:|:-----------------:|:--------------:|:----------:|:----------:|:----------------:|:-----------------:|:------------:|:------------:|:--------------:|:--------:|:---------------------:|:---------------:|:----------------:|:----------:|:---------------:|:---------:|:---------------:|:---------:|:----------------------:|:----------------:|
| 0.0433        | 1.0   | 2659  | 0.0423          | 0.7607          | 0.7798       | 0.7702   | 0.7759   | 0.6398          | 0.5561       | 0.5585   | 0.5535   | 0.9832            | 0.9832         | 0.9832     | 0.9832     | 0.9832           | 0.7615            | 0.9887       | 0.9908       | 0.9671         | 0.8211   | 0.9878                | 0.4354          | 0.9805           | 0.8265     | 0.9974          | 0.2243    | 0.9746          | 0.7602    | 0.9918                 | 0.2834           |
| 0.0366        | 2.0   | 5318  | 0.0393          | 0.7758          | 0.7858       | 0.7808   | 0.7838   | 0.6349          | 0.5972       | 0.6105   | 0.6015   | 0.9841            | 0.9841         | 0.9841     | 0.9841     | 0.9841           | 0.7725            | 0.9897       | 0.9920       | 0.9678         | 0.8295   | 0.9899                | 0.3313          | 0.9816           | 0.8338     | 0.9974          | 0.4545    | 0.9763          | 0.7662    | 0.9914                 | 0.4480           |
| 0.0305        | 3.0   | 7977  | 0.0399          | 0.7608          | 0.8186       | 0.7887   | 0.8064   | 0.6621          | 0.6856       | 0.6715   | 0.6794   | 0.9842            | 0.9842         | 0.9842     | 0.9842     | 0.9842           | 0.7810            | 0.9897       | 0.9919       | 0.9662         | 0.8272   | 0.9892                | 0.4772          | 0.9815           | 0.8347     | 0.9977          | 0.5629    | 0.9772          | 0.7740    | 0.9931                 | 0.5528           |
| 0.0263        | 4.0   | 10636 | 0.0435          | 0.7333          | 0.8336       | 0.7803   | 0.8114   | 0.6395          | 0.7039       | 0.6687   | 0.6890   | 0.9830            | 0.9830         | 0.9830     | 0.9830     | 0.9830           | 0.7732            | 0.9897       | 0.9912       | 0.9608         | 0.8083   | 0.9898                | 0.4791          | 0.9812           | 0.8319     | 0.9972          | 0.5368    | 0.9756          | 0.7700    | 0.9935                 | 0.5861           |
| 0.0218        | 5.0   | 13295 | 0.0456          | 0.7480          | 0.8108       | 0.7781   | 0.7974   | 0.6661          | 0.6720       | 0.6662   | 0.6691   | 0.9833            | 0.9833         | 0.9833     | 0.9833     | 0.9833           | 0.7701            | 0.9890       | 0.9907       | 0.9612         | 0.8071   | 0.9894                | 0.4642          | 0.9823           | 0.8354     | 0.9977          | 0.5325    | 0.9754          | 0.7613    | 0.9936                 | 0.5968           |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.9.0+cu102
- Datasets 1.9.0
- Tokenizers 0.10.3
