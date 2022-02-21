---
language: "en"
tags:
- buy-intent
- sell-intent
- consumer-intent
widget:
- text: "Flutoprazepam (Restas) is a drug which is a benzodiazepine. It was patented in Japan by Sumitomo."
---
# Chemical vs Pharmaceutical Domain Document Classifier
Chemical domain language model finetuned on 13K Chemical, and 14K Pharma Wikipedia articles broken into paragraphs.

| Train Loss    | Validation Acc. | Test Acc.|
| ------------- |:-------------: | -----:   |
| 0.17      | 0.928  | 0.927    |
# Dataset
Dataset with splits can be found @ [https://www.kaggle.com/shahrukhkhan/pharma-vs-chemicals-domain-classification](https://www.kaggle.com/shahrukhkhan/pharma-vs-chemicals-domain-classification)

# Label Mappings
LABEL_0 => **"PHARMACEUTICAL"** <br/>
LABEL_1 => **"CHEMICAL"**

## Usage in Transformers

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("recobo/chemical-bert-uncased-pharmaceutical-chemical-classifier")

model = AutoModelForSequenceClassification.from_pretrained("recobo/chemical-bert-uncased-pharmaceutical-chemical-classifier")
```