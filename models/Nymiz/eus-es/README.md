---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: test
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# test

This model is a fine-tuned version of [bert-base-multilingual-uncased](https://huggingface.co/bert-base-multilingual-uncased) on the [Euskera-Spanish](https://huggingface.co/datasets/Nymiz/euskera-spanish) dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0439
- Precision: 0.9565
- Recall: 0.9429
- F1: 0.9496
- Accuracy: 0.9931

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
- num_epochs: 40

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 14   | 0.4269          | 0.0       | 0.0    | 0.0    | 0.8945   |
| No log        | 2.0   | 28   | 0.1628          | 0.5143    | 0.5143 | 0.5143 | 0.9599   |
| No log        | 3.0   | 42   | 0.0969          | 0.7730    | 0.7786 | 0.7758 | 0.9815   |
| No log        | 4.0   | 56   | 0.0550          | 0.7267    | 0.7786 | 0.7517 | 0.9890   |
| No log        | 5.0   | 70   | 0.0582          | 0.8643    | 0.8643 | 0.8643 | 0.9894   |
| No log        | 6.0   | 84   | 0.0420          | 0.8936    | 0.9    | 0.8968 | 0.9918   |
| No log        | 7.0   | 98   | 0.0314          | 0.8690    | 0.9    | 0.8842 | 0.9931   |
| No log        | 8.0   | 112  | 0.0396          | 0.8601    | 0.8786 | 0.8693 | 0.9911   |
| No log        | 9.0   | 126  | 0.0476          | 0.9       | 0.9    | 0.9    | 0.9924   |
| No log        | 10.0  | 140  | 0.0510          | 0.8881    | 0.9071 | 0.8975 | 0.9921   |
| No log        | 11.0  | 154  | 0.0523          | 0.9270    | 0.9071 | 0.9170 | 0.9916   |
| No log        | 12.0  | 168  | 0.0391          | 0.9034    | 0.9357 | 0.9193 | 0.9928   |
| No log        | 13.0  | 182  | 0.0378          | 0.9167    | 0.9429 | 0.9296 | 0.9928   |
| No log        | 14.0  | 196  | 0.0419          | 0.9161    | 0.9357 | 0.9258 | 0.9926   |
| No log        | 15.0  | 210  | 0.0490          | 0.9286    | 0.9286 | 0.9286 | 0.9921   |
| No log        | 16.0  | 224  | 0.0526          | 0.9155    | 0.9286 | 0.9220 | 0.9918   |
| No log        | 17.0  | 238  | 0.0504          | 0.9091    | 0.9286 | 0.9187 | 0.9916   |
| No log        | 18.0  | 252  | 0.0516          | 0.9149    | 0.9214 | 0.9181 | 0.9923   |
| No log        | 19.0  | 266  | 0.0497          | 0.9291    | 0.9357 | 0.9324 | 0.9926   |
| No log        | 20.0  | 280  | 0.0599          | 0.9220    | 0.9286 | 0.9253 | 0.9916   |
| No log        | 21.0  | 294  | 0.0548          | 0.9281    | 0.9214 | 0.9247 | 0.9923   |
| No log        | 22.0  | 308  | 0.0430          | 0.9424    | 0.9357 | 0.9391 | 0.9934   |
| No log        | 23.0  | 322  | 0.0439          | 0.9565    | 0.9429 | 0.9496 | 0.9931   |
| No log        | 24.0  | 336  | 0.0501          | 0.9565    | 0.9429 | 0.9496 | 0.9931   |
| No log        | 25.0  | 350  | 0.0462          | 0.9496    | 0.9429 | 0.9462 | 0.9929   |
| No log        | 26.0  | 364  | 0.0479          | 0.9565    | 0.9429 | 0.9496 | 0.9931   |
| No log        | 27.0  | 378  | 0.0496          | 0.9429    | 0.9429 | 0.9429 | 0.9924   |
| No log        | 28.0  | 392  | 0.0446          | 0.9565    | 0.9429 | 0.9496 | 0.9931   |
| No log        | 29.0  | 406  | 0.0447          | 0.9496    | 0.9429 | 0.9462 | 0.9932   |
| No log        | 30.0  | 420  | 0.0491          | 0.9496    | 0.9429 | 0.9462 | 0.9928   |
| No log        | 31.0  | 434  | 0.0430          | 0.9167    | 0.9429 | 0.9296 | 0.9934   |
| No log        | 32.0  | 448  | 0.0530          | 0.9496    | 0.9429 | 0.9462 | 0.9929   |
| No log        | 33.0  | 462  | 0.0547          | 0.9496    | 0.9429 | 0.9462 | 0.9928   |
| No log        | 34.0  | 476  | 0.0515          | 0.9429    | 0.9429 | 0.9429 | 0.9929   |
| No log        | 35.0  | 490  | 0.0533          | 0.9429    | 0.9429 | 0.9429 | 0.9929   |
| 0.0625        | 36.0  | 504  | 0.0543          | 0.9496    | 0.9429 | 0.9462 | 0.9928   |
| 0.0625        | 37.0  | 518  | 0.0545          | 0.9496    | 0.9429 | 0.9462 | 0.9928   |
| 0.0625        | 38.0  | 532  | 0.0545          | 0.9357    | 0.9357 | 0.9357 | 0.9924   |
| 0.0625        | 39.0  | 546  | 0.0548          | 0.9357    | 0.9357 | 0.9357 | 0.9923   |
| 0.0625        | 40.0  | 560  | 0.0549          | 0.9357    | 0.9357 | 0.9357 | 0.9923   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
