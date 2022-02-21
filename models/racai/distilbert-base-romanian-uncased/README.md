---
language: ro
license: mit
datasets:
- oscar
- wikipedia
---


# Romanian DistilBERT

This repository contains the uncased Romanian DistilBERT (named Distil-RoBERT-base in the paper). The teacher model used for distillation is: [readerbench/RoBERT-base](https://huggingface.co/readerbench/RoBERT-base).

The model was introduced in [this paper](https://arxiv.org/abs/2112.12650). The adjacent code can be found
[here](https://github.com/racai-ai/Romanian-DistilBERT).

## Usage

```python
from transformers import AutoTokenizer, AutoModel

# load the tokenizer and the model
tokenizer = AutoTokenizer.from_pretrained("racai/distilbert-base-romanian-uncased")
model = AutoModel.from_pretrained("racai/distilbert-base-romanian-uncased")

# tokenize a test sentence
input_ids = tokenizer.encode("aceasta este o propoziție de test.", add_special_tokens=True, return_tensors="pt")

# run the tokens trough the model
outputs = model(input_ids)

print(outputs)
```

## Model Size

It is 35% smaller than its teacher `RoBERT-base`.

| Model                          | Size (MB) | Params (Millions) |
|--------------------------------|:---------:|:----------------:| 
| RoBERT-base    | 441 | 114 |
| distilbert-base-romanian-cased | 282 | 72 |

## Evaluation

We evaluated the model in comparison with the RoBERT-base on 5 Romanian tasks:

- **UPOS**: Universal Part of Speech (F1-macro)
- **XPOS**: Extended Part of Speech (F1-macro)
- **NER**: Named Entity Recognition (F1-macro)
- **SAPN**: Sentiment Anlaysis - Positive vs Negative (Accuracy)
- **SAR**: Sentiment Analysis - Rating (F1-macro)
- **DI**: Dialect identification  (F1-macro)
- **STS**: Semantic Textual Similarity (Pearson)

| Model                          | UPOS | XPOS | NER | SAPN | SAR | DI | STS |
|--------------------------------|:----:|:----:|:---:|:----:|:---:|:--:|:---:|
| RoBERT-base | 98.02 | 97.15 | 85.14 | 98.30 | 79.40 | 96.07 | 81.18 |
| distilbert-base-romanian-uncased | 97.12 | 95.79 | 83.11 | 98.01 | 79.58 | 96.11 | 79.80 |

### BibTeX entry and citation info
```bibtex
@article{avram2021distilling,
  title={Distilling the Knowledge of Romanian BERTs Using Multiple Teachers},
  author={Andrei-Marius Avram and Darius Catrina and Dumitru-Clementin Cercel and Mihai Dascălu and Traian Rebedea and Vasile Păiş and Dan Tufiş},
  journal={ArXiv},
  year={2021},
  volume={abs/2112.12650}
}
```