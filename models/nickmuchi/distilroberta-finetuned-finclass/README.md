---
license: apache-2.0
language: "en"
tags:
- financial-sentiment-analysis
- sentiment-analysis
- sentence_50agree
- generated_from_trainer
- financial
- stocks
- sentiment
datasets:
- financial_phrasebank
- Kaggle Self label
- nickmuchi/financial-classification
metrics:
- f1
widget:
- text: "The USD rallied by 10% last night"
  example_title: "Bullish Sentiment"
- text: "Covid-19 cases have been increasing over the past few months"
  example_title: "Bearish Sentiment"
- text: "the USD has been trending lower"
  example_title: "Mildly Bearish Sentiment"
model-index:
- name: distilroberta-finetuned-finclass
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: financial_phrasebank
      type: finance
      args: sentence_50agree
    metrics:
    - type: F1
      name: F1
      value: 0.8835
    - type: accuracy
      name: accuracy
      value: 0.89
---

# distilroberta-finetuned-finclass

This model is a fine-tuned version of [distilroberta-base](https://huggingface.co/distilroberta-base) on the sentence_50Agree [financial-phrasebank + Kaggle Dataset](https://huggingface.co/datasets/nickmuchi/financial-classification). The Kaggle dataset includes Covid-19 sentiment data and can be found here: [sentiment-classification-selflabel-dataset](https://www.kaggle.com/percyzheng/sentiment-classification-selflabel-dataset).
It achieves the following results on the evaluation set:
- Loss: 0.4463
- F1: 0.8835

## Model description

Model determines the financial sentiment of given text. Given the unbalanced distribution of the class labels, the weights were adjusted to pay attention to the less sampled labels which should increase overall performance.

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | F1     |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.7309        | 1.0   | 72   | 0.3671          | 0.8441 |
| 0.3757        | 2.0   | 144  | 0.3199          | 0.8709 |
| 0.3054        | 3.0   | 216  | 0.3096          | 0.8678 |
| 0.2229        | 4.0   | 288  | 0.3776          | 0.8390 |
| 0.1744        | 5.0   | 360  | 0.3678          | 0.8723 |
| 0.1436        | 6.0   | 432  | 0.3728          | 0.8758 |
| 0.1044        | 7.0   | 504  | 0.4116          | 0.8744 |
| 0.0931        | 8.0   | 576  | 0.4148          | 0.8761 |
| 0.0683        | 9.0   | 648  | 0.4423          | 0.8837 |
| 0.0611        | 10.0  | 720  | 0.4463          | 0.8835 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
