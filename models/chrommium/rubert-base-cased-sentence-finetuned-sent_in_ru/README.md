---
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: rubert-base-cased-sentence-finetuned-sent_in_ru
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# rubert-base-cased-sentence-finetuned-sent_in_ru

This model is a fine-tuned version of [DeepPavlov/rubert-base-cased-sentence](https://huggingface.co/DeepPavlov/rubert-base-cased-sentence) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3503
- Accuracy: 0.6884
- F1: 0.6875

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 15
- eval_batch_size: 15
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 25

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 441   | 0.7397          | 0.6630   | 0.6530 |
| 0.771         | 2.0   | 882   | 0.7143          | 0.6909   | 0.6905 |
| 0.5449        | 3.0   | 1323  | 0.8385          | 0.6897   | 0.6870 |
| 0.3795        | 4.0   | 1764  | 0.8851          | 0.6939   | 0.6914 |
| 0.3059        | 5.0   | 2205  | 1.0728          | 0.6933   | 0.6953 |
| 0.2673        | 6.0   | 2646  | 1.0673          | 0.7060   | 0.7020 |
| 0.2358        | 7.0   | 3087  | 1.5200          | 0.6830   | 0.6829 |
| 0.2069        | 8.0   | 3528  | 1.3439          | 0.7024   | 0.7016 |
| 0.2069        | 9.0   | 3969  | 1.3545          | 0.6830   | 0.6833 |
| 0.1724        | 10.0  | 4410  | 1.5591          | 0.6927   | 0.6902 |
| 0.1525        | 11.0  | 4851  | 1.6425          | 0.6818   | 0.6823 |
| 0.131         | 12.0  | 5292  | 1.8999          | 0.6836   | 0.6775 |
| 0.1253        | 13.0  | 5733  | 1.6959          | 0.6884   | 0.6877 |
| 0.1132        | 14.0  | 6174  | 1.9561          | 0.6776   | 0.6803 |
| 0.0951        | 15.0  | 6615  | 2.0356          | 0.6763   | 0.6754 |
| 0.1009        | 16.0  | 7056  | 1.7995          | 0.6842   | 0.6741 |
| 0.1009        | 17.0  | 7497  | 2.0638          | 0.6884   | 0.6811 |
| 0.0817        | 18.0  | 7938  | 2.1686          | 0.6884   | 0.6859 |
| 0.0691        | 19.0  | 8379  | 2.0874          | 0.6878   | 0.6889 |
| 0.0656        | 20.0  | 8820  | 2.1772          | 0.6854   | 0.6817 |
| 0.0652        | 21.0  | 9261  | 2.4018          | 0.6872   | 0.6896 |
| 0.0608        | 22.0  | 9702  | 2.2074          | 0.6770   | 0.6656 |
| 0.0677        | 23.0  | 10143 | 2.2101          | 0.6848   | 0.6793 |
| 0.0559        | 24.0  | 10584 | 2.2920          | 0.6848   | 0.6835 |
| 0.0524        | 25.0  | 11025 | 2.3503          | 0.6884   | 0.6875 |


### Framework versions

- Transformers 4.11.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
