---
language: ko
tags:
  - korean
  - lassl

---

# LASSL gpt2-ko-small
Pretrained `gpt2-ko-small` on korean language was trained by [LASSL](https://github.com/lassl/lassl) framework.

## How to use

```python
from transformers import AutoModel, AutoTokenizer
model = AutoModel.from_pretrained("lassl/gpt2-ko-small")
tokenizer = AutoTokenizer.from_pretrained("lassl/gpt2-ko-small")
```
