---
language: eu
---

# byt5-basque

Pretrained from scratch on Euskara (Basque language) 
with ByT5, Google's new byte-level tokenizer strategy.

Corpus: eu.wikipedia.org as of March 2020 (TFDS)

Pretraining Notebook: https://colab.research.google.com/drive/19Afq7CI6cOi1DaTpnQhBbEbnBzLSFHbH

## Todos

Fine-tuning

The Wikipedia corpus is small for this language compared to web crawls. In the future I would add
OSCAR, if I can rewrite the script to accept those
as one TFDS dataset.

