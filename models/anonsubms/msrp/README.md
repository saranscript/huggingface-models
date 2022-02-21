---
language: en
tags:
- t5-small
datasets:
- Gigaword
- DUC2004
---

## Multi-Summary Reinforcement Learning for Unsupervised Length-Controllable Summarization

This model (MSRP) is trained on Gigaword data. 

### How to use

```python
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer("anonsubms/msrp")
model = AutoModel("anonsubms/msrp")
tar_len = "8"
doc = tar_len+": Replace me by a news article"
encoded_input = tokenizer(doc, return_tensors='pt')
summary = model(**encoded_input)
```
