---
language: sv
license: cc-by-4.0
tags:
- swedish
- roberta
pipeline_tag: fill-mask
widget:
- text: Meninged med livet är <mask>.
---
# Nordic Roberta Wikipedia
## Description
Nord roberta model trainined on the swedish danish and norwegian wikipedia.

## Evaluation
Evaluation on Named Entity recognition in Danish.

I finetuned each model on 3 epochs on DaNE, repeated it 5 times for each model, and calculated 95% confidence intervals for the means. Here are the results:

xlm-roberta-base : 88.01 +- 0.43

flax-community/nordic-roberta-wiki: 85.75 +- 0.69 (this model)

Maltehb/danish-bert-botxo: 85.38 +- 0.55

flax-community/roberta-base-danish:  80.14 +- 1.47

flax-community/roberta-base-scandinavian : 78.03 +- 3.02

Maltehb/-l-ctra-danish-electra-small-cased: 57.87 +- 3.19

NbAiLab/nb-bert-base : 30.24 +- 1.21

Randomly initialised RoBERTa model: 19.79 +- 2.00

Evaluation on Sentiment analysis in Dansish
Here are the results on test set, where each model has been trained 5 times, and the “+-” refers to a 95% confidence interval of the mean score:

Maltehb/danish-bert-botxo: 65.19 +- 0.53

NbAiLab/nb-bert-base : 63.80 +- 0.77

xlm-roberta-base : 63.55 +- 1.59

flax-community/nordic-roberta-wiki : 56.46 +- 1.77

flax-community/roberta-base-danish : 54.73 +- 8.96

flax-community/roberta-base-scandinavian : 44.28 +- 9.21

Maltehb/-l-ctra-danish-electra-small-cased : 47.78 +- 12.65

Randomly initialised RoBERTa model: 36.96 +- 1.02

Maltehb/roberta-base-scandinavian : 33.65 +- 8.32

## Model series
This model is part of a series of models training on TPU with Flax Jax during Huggingface Flax/Jax challenge.

## Gpt models

## Swedish Gpt
https://huggingface.co/birgermoell/swedish-gpt/

## Swedish gpt wiki
https://huggingface.co/flax-community/swe-gpt-wiki

# Nordic gpt wiki
https://huggingface.co/flax-community/nordic-gpt-wiki

## Dansk gpt wiki
https://huggingface.co/flax-community/dansk-gpt-wiki

## Norsk gpt wiki
https://huggingface.co/flax-community/norsk-gpt-wiki

## Roberta models

## Nordic Roberta Wiki
https://huggingface.co/flax-community/nordic-roberta-wiki

## Swe Roberta Wiki Oscar
https://huggingface.co/flax-community/swe-roberta-wiki-oscar

## Roberta Swedish Scandi
https://huggingface.co/birgermoell/roberta-swedish-scandi

## Roberta Swedish
https://huggingface.co/birgermoell/roberta-swedish

## Swedish T5 model
https://huggingface.co/birgermoell/t5-base-swedish


