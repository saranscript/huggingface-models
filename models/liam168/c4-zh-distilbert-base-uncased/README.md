---
language: zh
tags:
- exbert
license: apache-2.0
widget:
- text: "女人做得越纯粹，皮肤和身材就越好"
- text: "我喜欢篮球"
---

# liam168/c4-zh-distilbert-base-uncased

## Model description

用 ["女性","体育","文学","校园"]4类数据训练的分类模型。

## Overview

- **Language model**: DistilBERT
- **Model size**: 280M 
- **Language**: Chinese

## Example

```python
>>> from transformers import DistilBertForSequenceClassification , AutoTokenizer, pipeline

>>> model_name = "liam168/c4-zh-distilbert-base-uncased"
>>> class_num = 4
>>> ts_texts = ["女人做得越纯粹，皮肤和身材就越好", "我喜欢篮球"]
>>> model = DistilBertForSequenceClassification.from_pretrained(model_name, num_labels=class_num)
>>> tokenizer = AutoTokenizer.from_pretrained(model_name)
>>> classifier = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)
>>> classifier(ts_texts[0])
>>> classifier(ts_texts[1])

[{'label': 'Female', 'score': 0.9137857556343079}]
[{'label': 'Sports', 'score': 0.8206522464752197}]

```
