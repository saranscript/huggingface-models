---
language: multilingual

tags:
- biomedical
- lexical-semantics
- cross-lingual

datasets:
- UMLS

**[news]** A cross-lingual extension of SapBERT will appear in the main onference of **ACL 2021**! <br>
**[news]** SapBERT will appear in the conference proceedings of **NAACL 2021**!

### SapBERT-XLMR
SapBERT [(Liu et al. 2021)](https://arxiv.org/pdf/2010.11784.pdf) trained with [UMLS](https://www.nlm.nih.gov/research/umls/licensedcontent/umlsknowledgesources.html) 2020AB, using [xlm-roberta-large](https://huggingface.co/xlm-roberta-large) as the base model. Please use [CLS] as the representation of the input.

### Citation

```bibtex
@inproceedings{liu2021learning,
	title={Learning Domain-Specialised Representations for Cross-Lingual Biomedical Entity Linking},
	author={Liu, Fangyu and Vuli{\'c}, Ivan and Korhonen, Anna and Collier, Nigel},
	booktitle={Proceedings of ACL-IJCNLP 2021},
	month = aug,
	year={2021}
}
```
