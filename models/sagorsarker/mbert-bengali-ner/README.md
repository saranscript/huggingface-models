---
language: bn
tags:
- bengali-ner
- bengali
- bangla
- NER
license: mit
datasets:
- wikiann
- xtreme
---

# Multi-lingual BERT Bengali Name Entity Recognition
`mBERT-Bengali-NER` is a transformer-based Bengali NER model build with [bert-base-multilingual-uncased](https://huggingface.co/bert-base-multilingual-uncased) model and [Wikiann](https://huggingface.co/datasets/wikiann) Datasets.

## How to Use

```py
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("sagorsarker/mbert-bengali-ner")
model = AutoModelForTokenClassification.from_pretrained("sagorsarker/mbert-bengali-ner")

nlp = pipeline("ner", model=model, tokenizer=tokenizer)
example = "আমি জাহিদ এবং আমি ঢাকায় বাস করি।"

ner_results = nlp(example)
print(ner_results)
```

## Label and ID Mapping

| Label ID | Label |
| -------- | ----- |
|0 | O |
| 1 | B-PER |
| 2 | I-PER |
| 3 | B-ORG|
| 4 | I-ORG | 
| 5 | B-LOC |
| 6 | I-LOC |

## Training Details
- mBERT-Bengali-NER trained with [Wikiann](https://huggingface.co/datasets/wikiann) datasets
- mBERT-Bengali-NER trained with [transformers-token-classification](https://colab.research.google.com/github/huggingface/notebooks/blob/master/examples/token_classification.ipynb) script
- mBERT-Bengali-NER total trained 5 epochs.
- Trained in Kaggle GPU

## Evaluation Results
|Model | F1 | Precision | Recall | Accuracy | Loss |
| ---- | --- | --------- | ----- | -------- | --- |
|mBert-Bengali-NER | 0.97105 | 0.96769| 0.97443 | 0.97682 | 0.12511 |



  