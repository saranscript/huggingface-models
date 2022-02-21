---
language: 
- sk
tags:
- pos
license: cc
datasets:
- universal_dependencies
metrics:
- accuracy
widget:
- text: "Kde tá ľudská duša drieme?"
---


# POS tagger based on SlovakBERT

This is a POS tagger based on [SlovakBERT](https://huggingface.co/gerulata/slovakbert). The model uses [Universal POS tagset (UPOS)](https://universaldependencies.org/u/pos/). The model was fine-tuned using Slovak part of [Universal Dependencies dataset](https://universaldependencies.org/) [Zeman 2017] containing 10k manually annotated Slovak sentences.

## Results

The model was evaluated in [our paper](https://arxiv.org/abs/2109.15254) [Pikuliak et al 2021, Section 4.2]. It achieves \\(97.84\%\\) accuracy.

## Cite

```
@article{DBLP:journals/corr/abs-2109-15254,
  author    = {Mat{\'{u}}{\v{s}} Pikuliak and
               {\v{S}}tefan Grivalsk{\'{y}} and
               Martin Kon{\^{o}}pka and
               Miroslav Bl{\v{s}}t{\'{a}}k and
               Martin Tamajka and
               Viktor Bachrat{\'{y}} and
               Mari{\'{a}}n {\v{S}}imko and
               Pavol Bal{\'{a}}{\v{z}}ik and
               Michal Trnka and
               Filip Uhl{\'{a}}rik},
  title     = {SlovakBERT: Slovak Masked Language Model},
  journal   = {CoRR},
  volume    = {abs/2109.15254},
  year      = {2021},
  url       = {https://arxiv.org/abs/2109.15254},
  eprinttype = {arXiv},
  eprint    = {2109.15254},
}
```