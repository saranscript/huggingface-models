---
language: dv
---

# byt5-dv

Pretrained from scratch on Dhivei (language of the Maldives)
with ByT5, Google's new byte-level tokenizer strategy.

Corpus: dv.wikipedia.org as of March 2020 (TFDS)

Notebook - Pretraining on Wikipedia: https://colab.research.google.com/drive/19Afq7CI6cOi1DaTpnQhBbEbnBzLSFHbH

## Demo

Notebook - Finetuning on Maldivian news classification task: https://colab.research.google.com/drive/11u5SafR4bKICmArgDl6KQ9vqfYtDpyWp

Current performance:

- mBERT: 52%
- **byt5-dv**: 81%
- dv-wave (ELECTRA): 89%
- dv-muril: 90.7%
- dv-labse: 91.3-91.5%

Source of dataset: https://github.com/Sofwath/DhivehiDatasets

## Work in progress - todos

The Wikipedia corpus is too small for this language. In the future I would add
OSCAR and Sofwath's Maldivian corpus, if I can rewrite the script to accept those
as one TFDS dataset.

This is based on ByT5-small ... we should try a larger model

This needs more time for pretraining