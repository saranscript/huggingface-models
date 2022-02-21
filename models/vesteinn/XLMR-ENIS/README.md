----
language:
- is
- en
thumbnail: 
tags:
- icelandic
- xlmr
license: agpl-3.0 
datasets:
- ic3
- igc
- books3
pipeline: fill-mask
widget:
- text: "The capital of Iceland is<mask> ."
- text: "Höfuðborg Íslands er<mask> ."
---

# XLMR-ENIS

## Model description

This is a XLMR model trained on Icelandic and English text.

## Intended uses & limitations

This model is part of my MSc thesis about Q&A for Icelandic.

#### How to use

```python
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("vesteinn/XLMR-ENIS")

model = AutoModelForMaskedLM.from_pretrained("vesteinn/XLMR-ENIS")
```

#### Limitations and bias

## Training data

## Training procedure

## Eval results

### BibTeX entry and citation info

```bibtex
```

