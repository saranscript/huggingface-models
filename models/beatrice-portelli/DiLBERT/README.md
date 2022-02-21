---
language:
- en
tags:
- medical
- disease
- classification
---


# DiLBERT (Disease Language BERT)

The objective of this model was to obtain a specialized disease-related language, trained **from scratch**. <br>
We created a pre-training corpora starting from **ICD-11** entities, and enriched it with documents from **PubMed** and **Wikipedia** related to the same entities. <br>
Results of finetuning show that DiLBERT leads to comparable or higher accuracy scores on various classification tasks compared with other general-purpose or in-domain models (e.g., BioClinicalBERT, RoBERTa, XLNet).

Model released with the paper "**DiLBERT: Cheap Embeddings for Disease Related Medical NLP**". <br>
To summarize the practical implications of our work: we pre-trained and fine-tuned a domain specific BERT model on a small corpora, with comparable or better performance than state-of-the-art models.  
This approach may also simplify the development of models for languages different from English, due to the minor quantity of data needed for training.

### Composition of the pretraining corpus


| Source | Documents | Words |
|---|---:|---:|
| ICD-11 descriptions         | 34,676    | 1.0 million   |
| PubMed Title and Abstracts  | 852,550   | 184.6 million |
| Wikipedia pages             | 37,074    | 6.1 million   |

### Main repository

For more details check the main repo https://github.com/KevinRoitero/dilbert

# Usage

```python
from transformers import AutoModelForMaskedLM, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("beatrice-portelli/DiLBERT")
model = AutoModelForMaskedLM.from_pretrained("beatrice-portelli/DiLBERT")
```

# How to cite

```
@article{roitero2021dilbert,
  title={{DilBERT}: Cheap Embeddings for Disease Related Medical NLP},
  author={Roitero, Kevin and Portelli, Beatrice and Popescu, Mihai Horia and Della Mea, Vincenzo},
  journal={IEEE Access},
  volume={},
  pages={},
  year={2021},
  publisher={IEEE},
  note = {In Press}
}
```
