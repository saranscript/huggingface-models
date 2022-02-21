---
language: he
tags:
- roberta
- language model
datasets:
- oscar
---
# TavBERT base model
A Hebrew BERT-style masked language model operating over characters, pre-trained by masking spans of characters, similarly to SpanBERT (Joshi et al., 2020).

### How to use

```python
import numpy as np
import torch
from transformers import AutoModelForMaskedLM, AutoTokenizer

model = AutoModelForMaskedLM.from_pretrained("tau/tavbert-he")
tokenizer = AutoTokenizer.from_pretrained("tau/tavbert-he")

def mask_sentence(sent, span_len=5):
    start_pos = np.random.randint(0, len(sent) - span_len)
    masked_sent = sent[:start_pos] + '[MASK]' * span_len + sent[start_pos + span_len:]
    print("Masked sentence:", masked_sent)
    output = model(**tokenizer.encode_plus(masked_sent, 
                                           return_tensors='pt'))['logits'][0][1:-1]
    preds = [int(x) for x in torch.argmax(torch.softmax(output, axis=1), axis=1)[start_pos:start_pos + span_len]]
    pred_sent = sent[:start_pos] + ''.join(tokenizer.convert_ids_to_tokens(preds)) + sent[start_pos + span_len:]
    print("Model's prediction:", pred_sent)
```
## Training data
OSCAR (Ortiz, 2019) Hebrew section (10 GB text, 20 million sentences).

