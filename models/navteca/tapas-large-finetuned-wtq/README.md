---
datasets:
- sqa
- wikisql
- wtq
language: en
license: mit
pipeline_tag: table-question-answering
tags:
- tapas
- table-question-answering
---

# TAPAS large model fine-tuned on WikiTable Questions (WTQ)

TAPAS is a BERT-like transformers model pretrained on a large corpus of English data from Wikipedia in a self-supervised fashion. This means it was pretrained on the raw tables and associated texts only, with no humans labelling them in any way (which is why it can use lots of publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely, it was pretrained with two objectives:

- Masked language modeling (MLM): taking a (flattened) table and associated context, the model randomly masks 15% of the words in the input, then runs the entire (partially masked) sequence through the model. The model then has to predict the masked words. This is different from traditional recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like GPT which internally mask the future tokens. It allows the model to learn a bidirectional representation of a table and associated text.
- Intermediate pre-training: to encourage numerical reasoning on tables, the authors additionally pre-trained the model by creating a balanced dataset of millions of syntactically created training examples. Here, the model must predict (classify) whether a sentence is supported or refuted by the contents of a table. The training examples are created based on synthetic as well as counterfactual statements.

This way, the model learns an inner representation of the English language used in tables and associated texts, which can then be used to extract features useful for downstream tasks such as answering questions about a table, or determining whether a sentence is entailed or refuted by the contents of a table.

[TAPAS: Weakly Supervised Table Parsing via Pre-training](https://arxiv.org/abs/2004.02349)

## Training Data
This model was pre-trained on MLM and an additional step which the authors call intermediate pre-training, and then fine-tuned in a chain on [SQA](https://www.microsoft.com/en-us/download/details.aspx?id=54253), [WikiSQL](https://github.com/salesforce/WikiSQL) and finally [WTQ](https://github.com/ppasupat/WikiTableQuestions).

It can be used for answering questions related to a table.

## Usage and Performance
The trained model can be used like this:
```python
from transformers import AutoModelForTableQuestionAnswering, AutoTokenizer, pipeline

# Load model & tokenizer
tapas_model = AutoModelForTableQuestionAnswering.from_pretrained('navteca/tapas-large-finetuned-wtq')
tapas_tokenizer = AutoTokenizer.from_pretrained('navteca/tapas-large-finetuned-wtq')

# Get predictions
nlp = pipeline('table-question-answering', model=tapas_model, tokenizer=tapas_tokenizer)

result = nlp({
  'table': {
      'Repository': [
          'Transformers',
          'Datasets',
          'Tokenizers'
      ],
      'Stars': [
          '36542',
          '4512',
          '3934'
      ],
      'Contributors': [
          '651',
          '77',
          '34'
      ],
      'Programming language': [
          'Python',
          'Python',
          'Rust, Python and NodeJS'
      ]
  },
  'query': 'How many stars does the transformers repository have?'
})

print(result)

#{
#  "answer": "SUM > 36542",
#  "coordinates": [
#    [
#      0,
#      1
#    ]
#  ],
#  "cells": [
#    "36542"
#  ],
#  "aggregator": "SUM"
#}
```