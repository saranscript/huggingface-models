---
language: ro
license: mit
datasets:
- oscar
- wikipedia
---

# Romanian DistilBERT

This repository contains the a Romanian cased version of DistilBERT (named DistilMulti-BERT-base-ro in the paper) that was obtained by distilling an ensemble of two teacher models: [dumitrescustefan/bert-base-romanian-cased-v1](https://huggingface.co/dumitrescustefan/bert-base-romanian-cased-v1) and [readerbench/RoBERT-base](https://huggingface.co/readerbench/RoBERT-base). 

The model was introduced in [this paper](https://arxiv.org/abs/2112.12650). The adjacent code can be found
[here](https://github.com/racai-ai/Romanian-DistilBERT).

## Usage

```python
from transformers import AutoTokenizer, AutoModel

# load the tokenizer and the model
tokenizer = AutoTokenizer.from_pretrained("racai/distilbert-multi-base-romanian-cased")
model = AutoModel.from_pretrained("racai/distilbert-multi-base-romanian-cased")

# tokenize a test sentence
input_ids = tokenizer.encode("Aceasta este o propoziție de test.", add_special_tokens=True, return_tensors="pt")

# run the tokens trough the model
outputs = model(input_ids)

print(outputs)
```

## Model Size

The model is 35% smaller than `bert-base-romanian-cased-v1` and 30% smaller than `RoBERT-base`.

| Model                          | Size (MB) | Params (Millions) |
|--------------------------------|:---------:|:----------------:| 
| RoBERT-base | 441 | 114 |
| bert-base-romanian-cased-v1    | 477 | 124 |
| distilbert-multi-base-romanian-cased | 312 | 81 |

## Evaluation

We evaluated the model in comparison with its two teachers on 5 Romanian tasks:

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
| bert-base-romanian-cased-v1    | 98.00 | 96.46 | 85.88 | 98.07 | 79.61 | 95.58 | 80.30 |
| distilbert-multi-base-romanian-cased | 98.07 | 96.83 | 83.22 | 98.11 | 79.77 | 96.18 | 80.66 |

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