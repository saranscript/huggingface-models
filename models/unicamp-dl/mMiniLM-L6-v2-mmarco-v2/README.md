---
language: pt
license: mit
tags:
- msmarco
- miniLM
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
# mMiniLM-L6-v2 Reranker finetuned on mMARCO
## Introduction
mMiniLM-L6-v2-mmarco-v2 is a multilingual miniLM-based model finetuned on a multilingual version of MS MARCO passage dataset. This dataset, named mMARCO, is formed by passages in 9 different languages, translated from English MS MARCO passages collection.
In the v2 version, the datasets were translated using Google Translate. 
Further information about the dataset or the translation method can be found on our [**mMARCO: A Multilingual Version of MS MARCO Passage Ranking Dataset**](https://arxiv.org/abs/2108.13897) and [mMARCO](https://github.com/unicamp-dl/mMARCO) repository.
## Usage
```python
from transformers import AutoTokenizer, AutoModel

model_name = 'unicamp-dl/mMiniLM-L6-v2-mmarco-v2'
tokenizer  = AutoTokenizer.from_pretrained(model_name)
model      = AutoModel.from_pretrained(model_name)

```
# Citation
If you use mMiniLM-L6-v2-mmarco-v2, please cite:

    @misc{bonifacio2021mmarco,
      title={mMARCO: A Multilingual Version of MS MARCO Passage Ranking Dataset}, 
      author={Luiz Henrique Bonifacio and Vitor Jeronymo and Hugo Queiroz Abonizio and Israel Campiotti and Marzieh Fadaee and  and Roberto Lotufo and Rodrigo Nogueira},
      year={2021},
      eprint={2108.13897},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}


