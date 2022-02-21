---
language: ko
tags:
  - fill-mask
  - korean
  - lassl
mask_token: "[MASK]"
widget:
  - text: 대한민국의 수도는 [MASK] 입니다.
---

# LASSL bert-ko-small
Evaulation results will be released soon.

## How to use
```python
from transformers import AutoModel, AutoTokenizer
model = AutoModel.from_pretrained("lassl/bert-ko-small")
tokenizer = AutoTokenizer.from_pretrained("lassl/bert-ko-small")
```
