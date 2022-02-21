---
language: ko
tags:
- bart
license: mit
---

## KoBART-base-v2

With the addition of chatting data, the model is trained to handle the semantics of sequences longer than KoBART.

```python
from transformers import PreTrainedTokenizerFast, BartModel

tokenizer = PreTrainedTokenizerFast.from_pretrained('gogamza/kobart-base-v2')
model = BartModel.from_pretrained('gogamza/kobart-base-v2')
```

### Performance 

NSMC
- acc. : 0.901

