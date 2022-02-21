---
tags:
- generated_from_trainer
model-index:
- name: gpt-4-est-large
  results: []
---

# gpt-4-est-large

This is GPT for Estonian. Not GPT-4 :-) This is the large-size [GPT2](https://huggingface.co/docs/transformers/model_doc/gpt2) model, trained from scratch on 2.2 billion words (Estonian National Corpus + News Crawl + Common Crawl).

[Colab demo](https://colab.research.google.com/drive/1Bp7mGEQ1vmyqXPyXHV1yj68cRZEi2mq4?usp=sharing)

### Format

For training data was prepended with a text domain tag, and it should be added as prefix when using the model: >general<, >web<, >news<, >doaj< and >wiki< (standing for general texts, web crawled texts, news, article abstracts and wikipedia texts). Use the prefixes like this, e.g: ">web< Kas tead, et".

### Model details

- num. of layers: 24
- num. of heads: 24
- embedding size: 1536
- context size: 1024
- total size: 723.58M params

Further details to be added soon.

### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
