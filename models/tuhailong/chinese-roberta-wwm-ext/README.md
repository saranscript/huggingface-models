---
language: zh
tags:
- chinese-roberta-wwm-ext
datasets:
- dialogue
---
# Data
unsupervise train data is E-commerce dialogue.
## Model
model is chinese-roberta-wwm-ext
### Usage
```python
>>> from transformers import AutoTokenizer, AutoModel
>>> model = AutoModel.from_pretrained("tuhailong/chinese-roberta-wwm-ext")
>>> tokenizer = AutoTokenizer.from_pretrained("tuhailong/chinese-roberta-wwm-ext")
>>> sentences_str_list = ["今天天气不错的","天气不错的"]
>>> inputs = tokenizer(sentences_str_list,return_tensors="pt", padding='max_length', truncation=True, max_length=32)
>>> outputs = model(**inputs)
```