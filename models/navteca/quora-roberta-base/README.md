---
datasets:
- quora
language: en
license: mit
pipeline_tag: text-classification
tags:
- roberta
- text-classification
---
# Cross-Encoder for Quora Duplicate Questions Detection

This model was trained using [SentenceTransformers](https://sbert.net) [Cross-Encoder](https://www.sbert.net/examples/applications/cross-encoder/README.html) class.

This model uses [roberta-base](https://huggingface.co/roberta-base).

## Training Data

This model was trained on the [Quora Duplicate Questions](https://www.quora.com/q/quoradata/First-Quora-Dataset-Release-Question-Pairs) dataset.

The model will predict a score between 0 and 1: How likely the two given questions are duplicates.

Note: The model is not suitable to estimate the similarity of questions, e.g. the two questions "How to learn Java" and "How to learn Python" will result in a rahter low score, as these are not duplicates.

## Usage and Performance

The trained model can be used like this:

```python
from sentence_transformers import CrossEncoder

model = CrossEncoder('model_name')
scores = model.predict([('Question 1', 'Question 2'), ('Question 3', 'Question 4')])

print(scores)
```
