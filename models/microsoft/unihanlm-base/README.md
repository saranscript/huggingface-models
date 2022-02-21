---
language:
- zh
- ja
tags:
- crosslingual
license: apache-2.0
datasets:
- Wikipedia
---

# Unihan LM: Coarse-to-Fine Chinese-Japanese Language Model Pretraining with the Unihan Database

## Model description

Chinese and Japanese share many characters with similar surface morphology. To better utilize the shared knowledge across the languages, we propose UnihanLM, a self-supervised Chinese-Japanese pretrained masked language model (MLM) with a novel two-stage coarse-to-fine training approach. We exploit Unihan, a ready-made database constructed by linguistic experts to first merge morphologically similar characters into clusters. The resulting clusters are used to replace the original characters in sentences for the coarse-grained pretraining of the MLM. Then, we restore the clusters back to the original characters in sentences for the fine-grained pretraining to learn the representation of the specific characters. We conduct extensive experiments on a variety of Chinese and Japanese NLP benchmarks, showing that our proposed UnihanLM is effective on both mono- and cross-lingual Chinese and Japanese tasks, shedding light on a new path to exploit the homology of languages. [Paper](https://www.aclweb.org/anthology/2020.aacl-main.24/)

## Intended uses & limitations

#### How to use

Use it like how you use XLM :)

#### Limitations and bias

The training corpus is solely from Wikipedia so the model may perform worse on informal text data. Be careful with English words! The tokenizer would cut it to characters.

## Training data

We use Chinese and Japanese Wikipedia to train the model.

## Training procedure

Please refer to our paper: https://www.aclweb.org/anthology/2020.aacl-main.24/

## Eval results

Please refer to our paper: https://www.aclweb.org/anthology/2020.aacl-main.24/

### BibTeX entry and citation info

```bibtex
@inproceedings{xu-etal-2020-unihanlm,
    title = "{U}nihan{LM}: Coarse-to-Fine {C}hinese-{J}apanese Language Model Pretraining with the Unihan Database",
    author = "Xu, Canwen  and
      Ge, Tao  and
      Li, Chenliang  and
      Wei, Furu",
    booktitle = "Proceedings of the 1st Conference of the Asia-Pacific Chapter of the Association for Computational Linguistics and the 10th International Joint Conference on Natural Language Processing",
    month = dec,
    year = "2020",
    address = "Suzhou, China",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.aacl-main.24",
    pages = "201--211"
}
```