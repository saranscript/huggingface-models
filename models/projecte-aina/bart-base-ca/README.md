---
language: "ca"
license: apache-2.0
inference: false
---

# BART-Ca: The monolingual Catalan BART

## Model description

BART-ca is a transformer-based language model for the Catalan language and has been trained on a medium-size corpus collected from publicly available corpora and crawlers: the [Catalan Textual Corpus](https://huggingface.co/datasets/projecte-aina/catalan_textual_corpus).


## Tokenization

The training corpus has been tokenized using a byte version of [Byte-Pair Encoding (BPE)](https://github.com/openai/gpt-2) with a vocabulary size of 51,200 tokens. 

## BibTeX  citation

If you use any of these resources (datasets or models) in your work, please cite our latest preprint:

```bibtex
@misc{degibert2022sequencetosequence,
      title={Sequence-to-Sequence Resources for Catalan}, 
      author={Ona de Gibert and Ksenia Kharitonova and Blanca Calvo Figueras and Jordi Armengol-Estapé and Maite Melero},
      year={2022},
      eprint={2202.06871},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

## Funding
This work was funded by the [MT4All CEF](https://ec.europa.eu/inea/en/connecting-europe-facility/cef-telecom/2019-eu-ia-0031) project.