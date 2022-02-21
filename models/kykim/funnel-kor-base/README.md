---
language: ko
---

# Funnel-transformer base model for Korean

* 70GB Korean text dataset and 42000 lower-cased subwords are used
* Check the model performance and other language models for Korean in [github](https://github.com/kiyoungkim1/LM-kor)

```python
from transformers import FunnelTokenizer, FunnelModel

tokenizer = FunnelTokenizer.from_pretrained("kykim/funnel-kor-base")
model = FunnelModel.from_pretrained("kykim/funnel-kor-base")
```