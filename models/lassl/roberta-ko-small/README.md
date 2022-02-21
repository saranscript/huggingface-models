---
language: ko
tags:
  - korean
  - lassl
mask_token: "<mask>"
widget:
  - text: 대한민국의 수도는 <mask> 입니다.
---

# LASSL roberta-ko-small
Pretrained `roberta-ko-small` on korean language was trained by [LASSL](https://github.com/lassl/lassl) framework. Below performance was evaluated at 2021/12/15.

| nsmc | klue_nli | klue_sts | korquadv1 | klue_mrc | avg |
| ---- | -------- | -------- | --------- | ---- | -------- |
| 87.8846 | 66.3086 | 83.8353 | 83.1780 | 42.4585 | 72.7330 |

## How to use

```python
from transformers import AutoModel, AutoTokenizer
model = AutoModel.from_pretrained("lassl/roberta-ko-small")
tokenizer = AutoTokenizer.from_pretrained("lassl/roberta-ko-small")
```
