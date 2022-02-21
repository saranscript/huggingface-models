---
tags: autonlp
language: es
widget:
- text: "Y si me tomo una cerveza
Vuelves a mi cabeza
Y empiezo a recordarte
Es que me gusta cómo besas
Con tu delicadeza
Puede ser que
Tú y yo, somos el uno para el otro
Que no dejo de pensarte
Quise olvidarte y tomé un poco
Y resultó extrañarte, yeah"
datasets:
- hectorcotelo/autonlp-data-spanish_songs
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 202661

## Validation Metrics

- Loss: 1.5369086265563965
- Accuracy: 0.30762817840766987
- Macro F1: 0.28034259092597485
- Micro F1: 0.30762817840766987
- Weighted F1: 0.28072818168048186
- Macro Precision: 0.3113843896292072
- Micro Precision: 0.30762817840766987
- Weighted Precision: 0.3128459166476807
- Macro Recall: 0.3071652685939504
- Micro Recall: 0.30762817840766987
- Weighted Recall: 0.30762817840766987


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/hectorcotelo/autonlp-spanish_songs-202661
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("hectorcotelo/autonlp-spanish_songs-202661", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("hectorcotelo/autonlp-spanish_songs-202661", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```