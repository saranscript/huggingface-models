---
language:
- ga
license: apache-2.0
tags:
- irish
- electra
widget:
- text: "Ceoltóir [MASK] ab ea Johnny Cash."
---

# gaELECTRA
[gaELECTRA](https://arxiv.org/abs/2107.12930) is an ELECTRA model trained on 7.9M Irish sentences. For more details, including the hyperparameters and pretraining corpora used please refer to our paper. For fine-tuning this model on a token classification task, e.g. Named Entity Recognition, use the discriminator model.

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