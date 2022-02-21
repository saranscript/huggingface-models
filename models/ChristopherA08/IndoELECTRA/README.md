---
language: id
datasets:
- oscar
---
# IndoBERT (Indonesian BERT Model)

## Model description
ELECTRA is a new method for self-supervised language representation learning. This repository contains the pre-trained Electra Base model (tensorflow 1.15.0) trained in a Large Indonesian corpus (~16GB of raw text | ~2B indonesian words).
IndoELECTRA is a pre-trained language model based on ELECTRA architecture for the Indonesian Language. 

This model is base version which use electra-base config.

## Intended uses & limitations

#### How to use

```python
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("ChristopherA08/IndoELECTRA")
model = AutoModel.from_pretrained("ChristopherA08/IndoELECTRA")
tokenizer.encode("hai aku mau makan.")
[2, 8078, 1785, 2318, 1946, 18, 4]
```

## Training procedure

The training of the model has been performed using Google's original Tensorflow code on eight core Google Cloud TPU v2.
We used a Google Cloud Storage bucket, for persistent storage of training data and models.

