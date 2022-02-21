

# BERTOverflow

## Model description

We pre-trained BERT-base model on 152 million sentences from the StackOverflow's 10 year archive. More details of this model can be found in our ACL 2020 paper: [Code and Named Entity Recognition in StackOverflow](https://www.aclweb.org/anthology/2020.acl-main.443/). 




#### How to use

```python
from transformers import *
import torch

tokenizer = AutoTokenizer.from_pretrained("lanwuwei/BERTOverflow_stackoverflow_github")
model = AutoModelForTokenClassification.from_pretrained("lanwuwei/BERTOverflow_stackoverflow_github")

```



### BibTeX entry and citation info

```bibtex
@inproceedings{tabassum2020code,
    title={Code and Named Entity Recognition in StackOverflow},
    author={Tabassum, Jeniya  and Maddela, Mounica  and Xu, Wei and Ritter, Alan },
    booktitle = {Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics (ACL)},
    url={https://www.aclweb.org/anthology/2020.acl-main.443/}
    year = {2020},
}
```
