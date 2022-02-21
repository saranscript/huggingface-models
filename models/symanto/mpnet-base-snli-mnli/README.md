---
language: 
  - en
datasets:
- SNLI
- MNLI
tags:
- zero-shot-classification
---


A cross-attention NLI model trained for zero-shot and few-shot text classification.

The base model is [mpnet-base](https://huggingface.co/microsoft/mpnet-base), trained with the code from [here](https://github.com/facebookresearch/anli);
on [SNLI](https://nlp.stanford.edu/projects/snli/) and [MNLI](https://cims.nyu.edu/~sbowman/multinli/).

Usage:

```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer
import torch
import numpy as np

model = AutoModelForSequenceClassification.from_pretrained("symanto/mpnet-base-snli-mnli")
tokenizer = AutoTokenizer.from_pretrained("symanto/mpnet-base-snli-mnli")

input_pairs = [("I like this pizza.", "The sentence is positive."), ("I like this pizza.", "The sentence is negative.")]
inputs = tokenizer(["</s></s>".join(input_pair) for input_pair in input_pairs], return_tensors="pt")
logits = model(**inputs).logits
probs =  torch.softmax(logits, dim=1).tolist()
print("probs", probs)
np.testing.assert_almost_equal(probs, [[0.86, 0.14, 0.00], [0.16, 0.15, 0.69]], decimal=2)
```
