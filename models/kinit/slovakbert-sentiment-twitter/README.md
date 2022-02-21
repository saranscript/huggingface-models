---
language: 
- sk
tags:
- twitter
- sentiment-analysis
license: cc
metrics:
- f1
widget:
- text: "Najkrajšia vianočná reklama: Toto milé video vám vykúzli čarovnú atmosféru: Vianoce sa nezadržateľne blížia."
- text: "A opäť sa objavili nebezpečné výrobky. Pozrite sa, či ich nemáte doma"
---


# Sentiment Analysis model based on SlovakBERT

This is a sentiment analysis classifier based on [SlovakBERT](https://huggingface.co/gerulata/slovakbert). The model can distinguish three level of sentiment:

- `-1` - Negative sentiment
- `0` - Neutral sentiment
- `1` - Positive setiment

The model was fine-tuned using Slovak part of [Multilingual Twitter Sentiment Analysis Dataset](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0155036) [Mozetič et al 2016] containing 50k manually annotated Slovak tweets. As such, it is fine-tuned for tweets and it is not advised to use the model for general-purpose sentiment analysis.

## Results

The model was evaluated in [our paper](https://arxiv.org/abs/2109.15254) [Pikuliak et al 2021, Section 4.4]. It achieves \\(0.67\\) F1-score on the original dataset and \\(0.58\\) F1-score on general reviews dataset.

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