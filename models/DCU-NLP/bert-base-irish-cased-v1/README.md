---
language:
- ga
license: apache-2.0
tags:
- irish
- bert
widget:
- text: "Ceoltóir [MASK] ab ea Johnny Cash."
---

# gaBERT

[gaBERT](https://arxiv.org/abs/2107.12930) is a BERT-base model trained on 7.9M Irish sentences. For more details, including the hyperparameters and pretraining corpora used please refer to our paper.

### How to use gaBERT with HuggingFace

```
from transformers import AutoModelWithLMHead, AutoTokenizer
import torch

tokenizer = AutoTokenizer.from_pretrained("DCU-NLP/bert-base-irish-cased-v1")
model = AutoModelWithLMHead.from_pretrained("DCU-NLP/bert-base-irish-cased-v1")

sequence = f"Ceoltóir {tokenizer.mask_token} ab ea Johnny Cash."

input = tokenizer.encode(sequence, return_tensors="pt")
mask_token_index = torch.where(input == tokenizer.mask_token_id)[1]

token_logits = model(input)[0]
mask_token_logits = token_logits[0, mask_token_index, :]

top_5_tokens = torch.topk(mask_token_logits, 5, dim=1).indices[0].tolist()

for token in top_5_tokens:
    print(sequence.replace(tokenizer.mask_token, tokenizer.decode([token])))
```

### Limitations and bias
Some data used to pretrain gaBERT was scraped from the web which potentially contains ethically problematic text (bias, hate, adult content, etc.). Consequently, downstream tasks/applications using gaBERT should be thoroughly tested with respect to ethical considerations.

### BibTeX entry and citation info

If you use this model in your research, please consider citing our paper:

```
@article{DBLP:journals/corr/abs-2107-12930,
  author    = {James Barry and
               Joachim Wagner and
               Lauren Cassidy and
               Alan Cowap and
               Teresa Lynn and
               Abigail Walsh and
               M{\'{\i}}che{\'{a}}l J. {\'{O}} Meachair and
               Jennifer Foster},
  title     = {gaBERT - an Irish Language Model},
  journal   = {CoRR},
  volume    = {abs/2107.12930},
  year      = {2021},
  url       = {https://arxiv.org/abs/2107.12930},
  archivePrefix = {arXiv},
  eprint    = {2107.12930},
  timestamp = {Fri, 30 Jul 2021 13:03:06 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2107-12930.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```