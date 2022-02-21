---
language: 
  - ar
  - bg
  - de
  - el
  - en
  - es
  - fr
  - ru
  - th
  - tr
  - ur
  - vn
  - zh
datasets:
- SNLI
- MNLI
- ANLI
- XNLI
tags:
- zero-shot-classification
---


A cross-attention NLI model trained for zero-shot and few-shot text classification.

The base model is [xlm-roberta-base](https://huggingface.co/xlm-roberta-base), trained with the code from [here](https://github.com/facebookresearch/anli);
on [SNLI](https://nlp.stanford.edu/projects/snli/), [MNLI](https://cims.nyu.edu/~sbowman/multinli/), [ANLI](https://github.com/facebookresearch/anli) and [XNLI](https://github.com/facebookresearch/XNLI).

Usage:

```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer
import torch
import numpy as np

model = AutoModelForSequenceClassification.from_pretrained("symanto/xlm-roberta-base-snli-mnli-anli-xnli")
tokenizer = AutoTokenizer.from_pretrained("symanto/xlm-roberta-base-snli-mnli-anli-xnli")

input_pairs = [
               ("I like this pizza.", "The sentence is positive."),
               ("I like this pizza.", "The sentence is negative."),
               ("I mag diese Pizza.", "Der Satz ist positiv."),
               ("I mag diese Pizza.", "Der Satz ist negativ."),
               ("Me gusta esta pizza.", "Esta frase es positivo."),
               ("Me gusta esta pizza.", "Esta frase es negativo."),
]
inputs = tokenizer(input_pairs, truncation="only_first", return_tensors="pt", padding=True)
logits = model(**inputs).logits
probs = torch.softmax(logits, dim=1)
probs = probs[..., [0]].tolist()
print("probs", probs)
np.testing.assert_almost_equal(probs, [[0.83], [0.04], [1.00], [0.00], [1.00], [0.00]], decimal=2)
```
