---
language: dv
---

# byt5-base-dv

Pretrained from scratch on Dhivei (language of the Maldives)
with ByT5, Google's new byte-level tokenizer strategy.

**Use byt5-dv for now; this is less accurate**

Corpus: Sofwath's Dhivehi corpus https://github.com/Sofwath/DhivehiDatasets

Pretraining Notebook: 
https://colab.research.google.com/drive/1ERIZ1PyHn-yN_jo7dTQeODn22vrt-d1d?usp=sharing

## Fine-tuning Demo

On Dhivehi news classification task

https://colab.research.google.com/drive/11u5SafR4bKICmArgDl6KQ9vqfYtDpyWp?usp=sharing

## Issues

There was an issue with the vocabulary size, final layer, and/or accuracy on fine-tuning.
