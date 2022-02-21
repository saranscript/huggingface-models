---
language:
- en
datasets:
- pubmed
- chemical patent
- cooking recipe
---

## Proc-RoBERTa
Proc-RoBERTa is a pre-trained language model for procedural text. It was built by fine-tuning the RoBERTa-based model on a procedural corpus (PubMed articles/chemical patents/cooking recipes), which contains 1.05B tokens. More details can be found in the following [paper](https://arxiv.org/abs/2109.04711):

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
tokenizer = AutoTokenizer.from_pretrained("fbaigt/proc_roberta")
model = AutoModelForTokenClassification.from_pretrained("fbaigt/proc_roberta")
```

More usage details can be found [here](https://github.com/bflashcp3f/ProcBERT).