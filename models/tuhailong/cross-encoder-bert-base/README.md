---
language: zh
tags:
- sbert
datasets:
- dialogue
---

# Data
train data is similarity sentence data from E-commerce dialogue

## Model
model created by [sentence-tansformers](https://www.sbert.net/index.html)，model struct is cross-encoder

### Usage
```python
>>> from sentence_transformers.cross_encoder import CrossEncoder
>>> model = CrossEncoder('tuhailong/cross-encoder')
>>> scores = model.predict([["今天天气不错", "今天心情不错"]])
>>> print(scores)
```