---
language:
- ar

datasets:
 - labr

tags:
 - labr

widget:
- text: "كتاب ممل جدا تضييع وقت"
- text: "اسلوب ممتع وشيق في الكتاب استمعت بالاحداث"

---

# BERT-LABR unbalanced
Arabic version bert model fine tuned on LABR dataset

## Data
The model were fine-tuned on ~63000 book reviews in arabic using bert large arabic


## Results
| class    | precision | recall | f1-score | Support |
|----------|-----------|--------|----------|---------|
| 0        | 0.8109    | 0.6832 | 0.7416   | 1670    |
| 1        | 0.9399    | 0.9689 | 0.9542   | 8541    |
| Accuracy |           |        | 0.9221   | 10211   |



## How to use

You can use these models by installing `torch` or `tensorflow` and Huggingface library `transformers`. And you can use it directly by initializing it like this:  

```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model_name="mofawzy/bert-labr-unbalanced"
model = AutoModelForSequenceClassification.from_pretrained(model_name,num_labels=2)
tokenizer = AutoTokenizer.from_pretrained(model_name)

```
