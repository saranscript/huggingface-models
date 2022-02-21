---
license: apache-2.0
tags:
model-index:
- name: data2vec-nlp-base
  results: []
---
# Data2Vec NLP Base

This model was converted from `fairseq`.  
The original weights can be found in https://dl.fbaipublicfiles.com/fairseq/data2vec/nlp_base.pt

Example usage:
```python
from transformers import RobertaTokenizer, Data2VecForSequenceClassification, Data2VecConfig
import torch

tokenizer = RobertaTokenizer.from_pretrained("roberta-large")
config = Data2VecConfig.from_pretrained("edugp/data2vec-nlp-base")
model = Data2VecForSequenceClassification.from_pretrained("edugp/data2vec-nlp-base", config=config)
# Fine-tune this model

inputs = tokenizer("Hello, my dog is cute", return_tensors="pt")
outputs = model(**inputs)

prediction_logits = outputs.logits
```
