---

language: ja

license: cc-by-sa-4.0

tags:

- finance

datasets:

- wikipedia
- securities reports
- summaries of financial results

widget:

- text: 流動[MASK]は1億円となりました。

---

# ELECTRA small Japanese finance generator

This is a [ELECTRA](https://github.com/google-research/electra) model pretrained on texts in the Japanese language.

The codes for the pretraining are available at [retarfi/language-pretraining](https://github.com/retarfi/language-pretraining/tree/v1.0).

## Model architecture

The model architecture is the same as ELECTRA small in the [original ELECTRA paper](https://arxiv.org/abs/2003.10555); 12 layers, 64 dimensions of hidden states, and 1 attention heads.

## Training Data

The models are trained on the Japanese version of Wikipedia.

The training corpus is generated from the Japanese version of Wikipedia, using Wikipedia dump file as of June 1, 2021. 

The Wikipedia corpus file is 2.9GB, consisting of approximately 20M sentences.

The financial corpus consists of 2 corpora:

- Summaries of financial results from October 9, 2012, to December 31, 2020

- Securities reports from February 8, 2018, to December 31, 2020

The financial corpus file is 5.2GB, consisting of approximately 27M sentences.

## Tokenization

The texts are first tokenized by MeCab with IPA dictionary and then split into subwords by the WordPiece algorithm.

The vocabulary size is 32768.

## Training

The models are trained with the same configuration as ELECTRA small in the [original ELECTRA paper](https://arxiv.org/abs/2003.10555); 128 tokens per instance, 128 instances per batch, and 1M training steps.

The size of the generator is 1/4 of the size of the discriminator.

## Citation

**There will be another paper for this pretrained model. Be sure to check here again when you cite.**

```
@inproceedings{bert_electra_japanese,
  title = {Construction and Validation of a Pre-Trained Language Model
Using Financial Documents}
  author = {Masahiro Suzuki and Hiroki Sakaji and Masanori Hirano and Kiyoshi Izumi},
  month = {oct},
  year = {2021},
  booktitle = {"Proceedings of JSAI Special Interest Group on Financial Infomatics (SIG-FIN) 27"}
}
```

## Licenses

The pretrained models are distributed under the terms of the [Creative Commons Attribution-ShareAlike 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

## Acknowledgments

This work was supported by JSPS KAKENHI Grant Number JP21K12010.
