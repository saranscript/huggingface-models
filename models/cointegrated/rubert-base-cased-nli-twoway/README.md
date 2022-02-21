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
- text: "Я хочу поехать в Австралию"
  candidate_labels: "спорт,путешествия,музыка,кино,книги,наука,политика"
  hypothesis_template: "Тема текста - {}." 
---
# RuBERT for NLI (natural language inference)

This is the [DeepPavlov/rubert-base-cased](https://huggingface.co/DeepPavlov/rubert-base-cased) fine-tuned to predict the logical relationship between two short texts: entailment or not entailment.

For more details, see the card for a similar model: https://huggingface.co/cointegrated/rubert-base-cased-nli-threeway

