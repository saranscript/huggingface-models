---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- bshlgrs/autonlp-data-old-data-trained
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 10022181

## Validation Metrics

- Loss: 0.369505375623703
- Accuracy: 0.8706206896551724
- Macro F1: 0.5410226656476808
- Micro F1: 0.8706206896551724
- Weighted F1: 0.8515634683886795
- Macro Precision: 0.5159711665622992
- Micro Precision: 0.8706206896551724
- Weighted Precision: 0.8346991124101657
- Macro Recall: 0.5711653346601209
- Micro Recall: 0.8706206896551724
- Weighted Recall: 0.8706206896551724


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/bshlgrs/autonlp-old-data-trained-10022181
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("bshlgrs/autonlp-old-data-trained-10022181", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("bshlgrs/autonlp-old-data-trained-10022181", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```