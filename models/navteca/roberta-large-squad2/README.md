---
datasets:
- squad_v2
language: en
license: mit
pipeline_tag: question-answering
tags:
- roberta
- question-answering
---
# Roberta large model for QA (SQuAD 2.0)

This model uses [roberta-large](https://huggingface.co/roberta-large).

## Training Data
The models have been trained on the [SQuAD 2.0](https://rajpurkar.github.io/SQuAD-explorer/) dataset.

It can be used for question answering task.

## Usage and Performance
The trained model can be used like this:
```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer, pipeline

# Load model & tokenizer
roberta_model = AutoModelForQuestionAnswering.from_pretrained('navteca/roberta-large-squad2')
roberta_tokenizer = AutoTokenizer.from_pretrained('navteca/roberta-large-squad2')

# Get predictions
nlp = pipeline('question-answering', model=roberta_model, tokenizer=roberta_tokenizer)

result = nlp({
    'question': 'How many people live in Berlin?',
    'context': 'Berlin had a population of 3,520,031 registered inhabitants in an area of 891.82 square kilometers.'
})

print(result)

#{
#  "answer": "3,520,031"
#  "end": 36,
#  "score": 0.96186668,
#  "start": 27,
#}
```
