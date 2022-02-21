---
language: te
---
# telugu_bertu

## Model description

This model is a BERT MLM model trained on Telugu. Please use it from the terminal as the web interface has encoding issues.

PS: If you find my model useful, I would appreciate a note from you as it would encourage me to continue improving it and also add new models.

## Intended uses & limitations

#### How to use

```python
from transformers import AutoModelWithLMHead, AutoTokenizer, pipeline
tokenizer = AutoTokenizer.from_pretrained("kuppuluri/telugu_bertu",
                                          clean_text=False,
                                          handle_chinese_chars=False,
                                          strip_accents=False,
                                          wordpieces_prefix='##')
model = AutoModelWithLMHead.from_pretrained("kuppuluri/telugu_bertu")
fill_mask = pipeline("fill-mask", model=model, tokenizer=tokenizer)
results = fill_mask("మక్దూంపల్లి పేరుతో చాలా [MASK] ఉన్నాయి.")
```
