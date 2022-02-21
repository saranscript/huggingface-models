---
language: en
tags:
- banking
- intent
- multiclass
datasets:
- banking77
widget:
- text: "How long until my transfer goes through?"
---
# distilroberta-base fine-tuned on banking77 dataset for intent classification
Test set accuray: 0.896

## How to use

```py
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

ckpt = 'mrm8488/distilroberta-finetuned-banking77'
tokenizer = AutoTokenizer.from_pretrained(ckpt)
model = AutoModelForSequenceClassification.from_pretrained(ckpt)

classifier = pipeline('text-classification', tokenizer=tokenizer, model=model)
classifier('What is the base of the exchange rates?')
# Output: [{'label': 'exchange_rate', 'score': 0.8509947657585144}]
```

> Created by [Manuel Romero/@mrm8488](https://twitter.com/mrm8488) | [LinkedIn](https://www.linkedin.com/in/manuel-romero-cs/)
> Made with <span style="color: #e25555;">&hearts;</span> in Spain