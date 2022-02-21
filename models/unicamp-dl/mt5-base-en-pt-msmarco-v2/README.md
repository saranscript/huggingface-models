---
language: pt
license: mit
tags:
- msmarco
- t5
- pytorch
- tensorflow
- pt
- pt-br
datasets:
- msmarco
widget:
- text: "Texto de exemplo em português"
inference: false
---
# mt5-base Reranker finetuned on mMARCO
## Introduction
mT5-base-en-pt-msmarco-v2 is a mT5-based model fine-tuned on a bilingual version of MS MARCO passage dataset. This bilingual dataset version is formed by the original MS MARCO dataset (in English) and a Portuguese translated version. In the v2 version, the Portuguese dataset was translated using Google Translate.
Further information about the dataset or the translation method can be found on our paper [**mMARCO: A Multilingual Version of MS MARCO Passage Ranking Dataset**](https://arxiv.org/abs/2108.13897) and [mMARCO](https://github.com/unicamp-dl/mMARCO) repository.

## Usage
```python

from transformers import T5Tokenizer, MT5ForConditionalGeneration

model_name = 'unicamp-dl/mt5-base-en-pt-msmarco-v2'
tokenizer  = T5Tokenizer.from_pretrained(model_name)
model      = MT5ForConditionalGeneration.from_pretrained(model_name)

```
# Citation
If you use mt5-base-en-pt-msmarco-v2, please cite:

    @misc{bonifacio2021mmarco,
      title={mMARCO: A Multilingual Version of MS MARCO Passage Ranking Dataset}, 
      author={Luiz Henrique Bonifacio and Vitor Jeronymo and Hugo Queiroz Abonizio and Israel Campiotti and Marzieh Fadaee and  and Roberto Lotufo and Rodrigo Nogueira},
      year={2021},
      eprint={2108.13897},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}

