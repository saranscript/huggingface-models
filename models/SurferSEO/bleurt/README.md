---
language: en
license: apache-2.0
---

# BLEURT

Pretrained model on English language. It was introduced in
[this paper](https://arxiv.org/pdf/2004.04696.pdf), described in [this blogpost](https://ai.googleblog.com/2020/05/evaluating-natural-language-generation.html) and first released in
[this repository](https://github.com/google-research/bleurt).

The team releasing BLEURT did not write a model card for this model so this model card has been written by
the Surfer team.

Original TensorFlow implementation has been converted to PyTorch with help of [this article](https://medium.com/huggingface/from-tensorflow-to-pytorch-265f40ef2a28) by Surfer team.

Visit us at [surferseo.com](https://surferseo.com).

### How to use

Since BLEURT is not implemented in transformers library yet, you have to import BleurtModel from bleurt_model.py

```python
import torch
from bleurt_model import BleurtModel
from transformers import BertTokenizerFast

model = BleurtModel.from_pretrained("SurferSEO/bleurt")
tokenizer = BertTokenizerFast.from_pretrained("SurferSEO/bleurt")

sentence_pairs = [("I love surfing.", "I'd like to surf.")]
encoded = tokenizer(sentence_pairs, padding=True, truncation=True, return_tensors="pt")
input_ids, attention_mask, token_type_ids = (
    encoded["input_ids"],
    encoded["attention_mask"],
    encoded["token_type_ids"],
)
with torch.set_grad_enabled(False):
    predictions = model(
        input_ids=input_ids,
        attention_mask=attention_mask,
        token_type_ids=token_type_ids,
    )
print(predictions)
```