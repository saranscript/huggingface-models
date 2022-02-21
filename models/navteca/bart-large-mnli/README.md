---
datasets:
- multi_nli
language: en
license: mit
pipeline_tag: zero-shot-classification
tags:
- bart
- zero-shot-classification
---
# Bart large model for NLI-based Zero Shot Text Classification

This model uses [bart-large](https://huggingface.co/facebook/bart-large).

## Training Data
This model was trained on the [MultiNLI (MNLI)](https://huggingface.co/datasets/multi_nli) dataset in the manner originally described in [Yin et al. 2019](https://arxiv.org/abs/1909.00161).

It can be used to predict whether a topic label can be assigned to a given sequence, whether or not the label has been seen before.

## Usage and Performance
The trained model can be used like this:
```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer, pipeline

# Load model & tokenizer
bart_model = AutoModelForSequenceClassification.from_pretrained('navteca/bart-large-mnli')
bart_tokenizer = AutoTokenizer.from_pretrained('navteca/bart-large-mnli')

# Get predictions
nlp = pipeline('zero-shot-classification', model=bart_model, tokenizer=bart_tokenizer)

sequence = 'One day I will see the world.'
candidate_labels = ['cooking', 'dancing', 'travel']

result = nlp(sequence, candidate_labels, multi_label=True)

print(result)

#{
#  "sequence": "One day I will see the world.",
#  "labels": [
#    "travel",
#    "dancing",
#    "cooking"
#  ],
#  "scores": [
#    0.9941897988319397,
#    0.0060537424869835,
#    0.0020010927692056
#  ]
#}
```