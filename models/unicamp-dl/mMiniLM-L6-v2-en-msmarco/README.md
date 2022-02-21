---
language: pt
license: mit
tags:
- msmarco
- miniLM
- pytorch
- tensorflow
- en
datasets:
- msmarco
widget:
- text: "Texto de exemplo em portuguÃªs"
inference: false
---
# mMiniLM-L6 Reranker finetuned on English MS MARCO
## Introduction
mMiniLM-L6-v2-en-msmarco is a multilingual miniLM-based model fine-tuned on English MS MARCO passage dataset. Further information about the dataset or the translation method can be found on our [**mMARCO: A Multilingual Version of MS MARCO Passage Ranking Dataset**](https://arxiv.org/abs/2108.13897) and [mMARCO](https://github.com/unicamp-dl/mMARCO) repository.
## Usage
```python
from transformers import AutoTokenizer, AutoModel

model_name = 'unicamp-dl/mMiniLM-L6-v2-en-msmarco'
tokenizer  = AutoTokenizer.from_pretrained(model_name)
model      = AutoModel.from_pretrained(model_name)

```
# Citation
If you use mMiniLM-L6-v2-en-msmarco, please cite:

    @misc{bonifacio2021mmarco,
      title={mMARCO: A Multilingual Version of the MS MARCO Passage Ranking Dataset}, 
      author={Luiz Henrique Bonifacio and Vitor Jeronymo and Hugo Queiroz Abonizio and Israel Campiotti and Marzieh Fadaee and  and Roberto Lotufo and Rodrigo Nogueira},
      year={2021},
      eprint={2108.13897},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}

