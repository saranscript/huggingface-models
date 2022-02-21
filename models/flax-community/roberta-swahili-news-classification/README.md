---
language: sw
widget:
- text: "Idris ameandika kwenye ukurasa wake wa Instagram akimkumbusha Diamond kutekeleza ahadi yake kumpigia Zari magoti kumuomba msamaha kama alivyowahi kueleza awali.Idris ameandika;"
datasets:
- flax-community/swahili-safi
---

## Swahili News Classification with RoBERTa


This model was trained using HuggingFace's Flax framework and is part of the [JAX/Flax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organized by [HuggingFace](https://huggingface.co). All training was done on a TPUv3-8 VM sponsored by the Google Cloud team.

This [model](https://huggingface.co/flax-community/roberta-swahili) was used as the base and fine-tuned for this task.

## How to use

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("flax-community/roberta-swahili-news-classification")

model = AutoModelForSequenceClassification.from_pretrained("flax-community/roberta-swahili-news-classification")
```

```
Eval metrics: {'accuracy': 0.9153416415986249}
```
