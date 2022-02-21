---
datasets:
- squad_v2
language: en
license: mit
pipeline_tag: question-answering
tags:
- electra
- question-answering
---
# Electra base model for QA (SQuAD 2.0)

This model uses [electra-base](https://huggingface.co/google/electra-base-discriminator).

## Training Data
The models have been trained on the [SQuAD 2.0](https://rajpurkar.github.io/SQuAD-explorer/) dataset.

It can be used for question answering task.

## Usage and Performance
The trained model can be used like this:
```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer, pipeline

# Load model & tokenizer
electra_model = AutoModelForQuestionAnswering.from_pretrained('navteca/electra-base-squad2')
electra_tokenizer = AutoTokenizer.from_pretrained('navteca/electra-base-squad2')

# Get predictions
nlp = pipeline('question-answering', model=electra_model, tokenizer=electra_tokenizer)

result = nlp({
    'question': 'How many people live in Berlin?',
    'context': 'Berlin had a population of 3,520,031 registered inhabitants in an area of 891.82 square kilometers.'
})

print(result)

#{
#  "answer": "3,520,031"
#  "end": 36,
#  "score": 0.99983448,
#  "start": 27,
#}
```
