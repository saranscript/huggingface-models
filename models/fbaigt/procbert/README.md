---
language:
- en
datasets:
- pubmed
- chemical patent
- cooking recipe
---

## ProcBERT
ProcBERT is a pre-trained language model specifically for procedural text. It was pre-trained on a large-scale procedural corpus (PubMed articles/chemical patents/cooking recipes) containing over 12B tokens and shows great performance on downstream tasks. More details can be found in the following [paper](https://arxiv.org/abs/2109.04711):

```
@inproceedings{bai-etal-2021-pre,
    title = "Pre-train or Annotate? Domain Adaptation with a Constrained Budget",
    author = "Bai, Fan  and
              Ritter, Alan  and
              Xu, Wei",
    booktitle = "Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing",
    month = nov,
    year = "2021",
    address = "Online and Punta Cana, Dominican Republic",
    publisher = "Association for Computational Linguistics",
}
```

## Usage
```
from transformers import *
tokenizer = AutoTokenizer.from_pretrained("fbaigt/procbert")
model = AutoModelForTokenClassification.from_pretrained("fbaigt/procbert")
```

More usage details can be found [here](https://github.com/bflashcp3f/ProcBERT).