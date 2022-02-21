---
language: 
- sv
tags:
- squad
license: apache-2.0
datasets:
- susumu2357/squad_v2_sv
metrics:
- squad_v2
---

# Swedish BERT Fine-tuned on SQuAD v2

This model is a fine-tuning checkpoint of Swedish BERT on SQuAD v2.

## Training data

Fine-tuning was done based on the pre-trained model [KB/bert-base-swedish-cased](https://huggingface.co/KB/bert-base-swedish-cased).

Training and dev datasets are our
[Swedish translation of SQuAD v2](https://github.com/susumu2357/SQuAD_v2_sv). 

[Here](https://huggingface.co/datasets/susumu2357/squad_v2_sv) is the HuggingFace Datasets.


## Hyperparameters
```
batch_size = 16
n_epochs = 2
max_seq_len = 386
learning_rate = 3e-5
warmup_steps = 2900    # warmup_proportion = 0.2
doc_stride=128
max_query_length=64
```

## Eval results
```
'exact': 66.72642524202223
'f1': 70.11149581003404
'total': 11156
'HasAns_exact': 55.574745730186144
'HasAns_f1': 62.821693965983044
'HasAns_total': 5211
'NoAns_exact': 76.50126156433979
'NoAns_f1': 76.50126156433979
'NoAns_total': 5945
```

## Limitations and bias

This model may contain biases due to mistranslations of the SQuAD dataset.

## BibTeX entry and citation info

```bibtex
@misc{svSQuADbert,
  author = {Susumu Okazawa},
  title = {Swedish BERT Fine-tuned on Swedish SQuAD 2.0},
  year = {2021},
  howpublished = {\url{https://huggingface.co/susumu2357/bert-base-swedish-squad2}},
}
```
