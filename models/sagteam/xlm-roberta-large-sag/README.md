---
language: multilingual
thumbnail: "url to a thumbnail used in social sharing"
tags: exbert
license: apache-2.0
---

# XLM-RoBERTa-large-sag

## Model description

This is a model based on the [XLM-RoBERTa large](https://huggingface.co/xlm-roberta-large) topology (provided by Facebook, see original [paper](https://arxiv.org/abs/1911.02116)) with additional training on two sets of medicine-domain texts: 
* about 250.000 text reviews on medicines (1000-tokens-long in average) collected from the site irecommend.ru;
* the raw part of the [RuDReC corpus](https://github.com/cimm-kzn/RuDReC) (about 1.4 million texts, see [paper](https://arxiv.org/abs/2004.03659)).

The XLM-RoBERTa-large calculations for one epoch on this data were performed using one Nvidia Tesla v100 and the Huggingface Transformers library. 

## BibTeX entry and citation info

If you have found our results helpful in your work, feel free to cite our publication as:

```
@article{sboev2021analysis,
  title={An analysis of full-size Russian complexly NER labelled corpus of Internet user reviews on the drugs based on deep learning and language neural nets},
  author={Sboev, Alexander and Sboeva, Sanna and Moloshnikov, Ivan and Gryaznov, Artem and Rybka, Roman and Naumov, Alexander and Selivanov, Anton and Rylkov, Gleb and Ilyin, Viacheslav},
  journal={arXiv preprint arXiv:2105.00059},
  year={2021}
}
```