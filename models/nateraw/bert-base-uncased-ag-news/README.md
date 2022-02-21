---
language:
- en
thumbnail: https://avatars3.githubusercontent.com/u/32437151?s=460&u=4ec59abc8d21d5feea3dab323d23a5860e6996a4&v=4
tags:
- text-classification
- ag_news
- pytorch
license: mit
datasets:
- ag_news
metrics:
- accuracy
---

# bert-base-uncased-ag-news

## Model description

`bert-base-uncased` finetuned on the AG News dataset using PyTorch Lightning. Sequence length 128, learning rate 2e-5, batch size 32, 4 T4 GPUs, 4 epochs. [The code can be found here](https://github.com/nateraw/hf-text-classification)

#### Limitations and bias

- Not the best model...

## Training data

Data came from HuggingFace's `datasets` package. The data can be viewed [on nlp viewer](https://huggingface.co/nlp/viewer/?dataset=ag_news).


## Training procedure

...

## Eval results

...