---
language: zh
widget: 
- text: "我喜欢下雨。"
- text: "我讨厌他。"
---

# liam168/c2-roberta-base-finetuned-dianping-chinese

## Model description

用中文对话情绪语料训练的模型，2分类：乐观和悲观。

## Overview

- **Language model**: BertForSequenceClassification
- **Model size**: 410M
- **Language**: Chinese

## Example

```python
>>> from transformers import AutoModelForSequenceClassification , AutoTokenizer, pipeline

>>> model_name = "liam168/c2-roberta-base-finetuned-dianping-chinese"
>>> class_num = 2
>>> ts_texts = ["我喜欢下雨。", "我讨厌他."]
>>> model = AutoModelForSequenceClassification.from_pretrained(model_name, num_labels=class_num)
>>> tokenizer = AutoTokenizer.from_pretrained(model_name)
>>> classifier = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)
>>> classifier(ts_texts[0])
>>> classifier(ts_texts[1])

[{'label': 'positive', 'score': 0.9973447918891907}]
[{'label': 'negative', 'score': 0.9972558617591858}]

```
