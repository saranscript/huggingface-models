---
widget:
- text: "Ну ты и придурок!!"
---

NER Toxic models

Fine-tuning [cointegrated/rubert-tiny-toxicity](https://huggingface.co/cointegrated/rubert-tiny-toxicity) model on data from [toxic_dataset_ner](https://huggingface.co/datasets/tesemnikov-av/toxic_dataset_ner)

language: RU

```python
!pip install transformers > /dev/null

from transformers import (
    AutoModelForTokenClassification, 
    AutoTokenizer, 
    pipeline
)

model = AutoModelForTokenClassification.from_pretrained('tesemnikov-av/rubert-ner-toxicity')
tokenizer = AutoTokenizer.from_pretrained('tesemnikov-av/rubert-ner-toxicity')


pipe = pipeline(model=model, tokenizer=tokenizer, task='ner', aggregation_strategy='average')
text = "Они охриневшие там все придурки!!"

print(text)
print(pipe(text))
```
