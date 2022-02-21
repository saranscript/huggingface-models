---
language: "en"
tags:
- twitter
- masked-token-prediction
- election2020
license: "gpl-3.0"
---

# Pre-trained BERT on Twitter US Political Election 2020

Pre-trained weights for [Knowledge Enhance Masked Language Model for Stance Detection](https://www.aclweb.org/anthology/2021.naacl-main.376), NAACL 2021.

We use the initialized weights from BERT-base (uncased) or `bert-base-uncased`.

# Training Data

This model is pre-trained on over 5 million English tweets about the 2020 US Presidential Election.

# Training Objective

This model is initialized with BERT-base and trained with normal MLM objective.

# Usage

This pre-trained language model **can be fine-tunned to any downstream task (e.g. classification)**.

Please see the [official repository](https://github.com/GU-DataLab/stance-detection-KE-MLM) for more detail.

```python
from transformers import BertTokenizer, BertForMaskedLM, pipeline
import torch

# choose GPU if available
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

# select mode path here
pretrained_LM_path = "kornosk/bert-political-election2020-twitter-mlm"

# load model
tokenizer = BertTokenizer.from_pretrained(pretrained_LM_path)
model = BertForMaskedLM.from_pretrained(pretrained_LM_path)

# fill mask
example = "Trump is the [MASK] of USA"
fill_mask = pipeline('fill-mask', model=model, tokenizer=tokenizer)

outputs = fill_mask(example)
print(outputs)

# see embeddings
inputs = tokenizer(example, return_tensors="pt")
outputs = model(**inputs)
print(outputs)

# OR you can use this model to train on your downstream task!
# please consider citing our paper if you feel this is useful :)
```

# Reference

- [Knowledge Enhance Masked Language Model for Stance Detection](https://www.aclweb.org/anthology/2021.naacl-main.376), NAACL 2021.

# Citation
```bibtex
@inproceedings{kawintiranon2021knowledge,
    title={Knowledge Enhanced Masked Language Model for Stance Detection},
    author={Kawintiranon, Kornraphop and Singh, Lisa},
    booktitle={Proceedings of the 2021 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies},
    year={2021},
    publisher={Association for Computational Linguistics},
    url={https://www.aclweb.org/anthology/2021.naacl-main.376}
}
```