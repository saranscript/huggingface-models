---
language: ru
pipeline_tag: zero-shot-classification
tags:
- rubert
- russian
- nli
- rte
- zero-shot-classification
widget:
- text: "Сервис отстойный, кормили невкусно"
  candidate_labels: "Мне понравилось, Мне не понравилось"
  hypothesis_template: "{}."
---
# RuBERT-tiny for NLI (natural language inference)

This is the [cointegrated/rubert-tiny](https://huggingface.co/cointegrated/rubert-tiny) model fine-tuned to predict the logical relationship between two short texts: entailment or not entailment.

For more details, see the card for a related model: https://huggingface.co/cointegrated/rubert-base-cased-nli-threeway

