---
language: id
tags:
  - indobert
  - indobenchmark
  - indonlu
license: mit
inference: true
datasets:
  - Indo4B
---

# IndoBERT-Lite Large Model (phase2 - uncased) Finetuned on IndoNLU SmSA dataset

Finetuned the IndoBERT-Lite Large Model (phase2 - uncased) model on the IndoNLU SmSA dataset following the procedues stated in the paper [IndoNLU: Benchmark and Resources for Evaluating Indonesian
Natural Language Understanding](https://arxiv.org/pdf/2009.05387.pdf).

## How to use

```python
from transformers import pipeline
classifier = pipeline("text-classification", 
                      model='tyqiangz/indobert-lite-large-p2-smsa', 
                      return_all_scores=True)
text = "Penyakit koronavirus 2019"
prediction = classifier(text)
prediction

"""
Output:
[[{'label': 'positive', 'score': 0.0006000096909701824},
  {'label': 'neutral', 'score': 0.01223431620746851},
  {'label': 'negative', 'score': 0.987165629863739}]]
"""
```

**Finetuning hyperparameters:**
- learning rate: 2e-5
- batch size: 16
- no. of epochs: 5
- max sequence length: 512
- random seed: 42

**Classes:**
- 0: positive
- 1: neutral
- 2: negative

**Performance metrics on SmSA validation dataset**
- Validation accuracy: 0.94
- Validation F1: 0.91
- Validation Recall: 0.91
- Validation Precision: 0.93

