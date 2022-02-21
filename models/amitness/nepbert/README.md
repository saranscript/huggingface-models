---
language:
- ne
thumbnail:
tags:
- roberta
- nepali-laguage-model
license: mit
datasets:
- cc100
widget:
- text: तिमीलाई कस्तो <mask>?
---

# nepbert

## Model description

Roberta trained from scratch on the Nepali CC-100 dataset with 12 million sentences.

## Intended uses & limitations

#### How to use

```python
from transformers import pipeline

pipe = pipeline(
    "fill-mask",
    model="amitness/nepbert",
    tokenizer="amitness/nepbert"
)
print(pipe(u"तिमीलाई कस्तो <mask>?"))
```

## Training data

The data was taken from the nepali language subset of CC-100 dataset.

## Training procedure
The model was trained on Google Colab using `1x Tesla V100`.