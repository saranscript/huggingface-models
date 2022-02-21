---
widget:
- text: "Prime Minister Hun Sen insisted that talks take place in Cambodia. </s><s> Cambodian leader Hun Sen rejected opposition parties' demands for talks outside the country."
---

# SuperPAL model

Summary-Source Proposition-level Alignment: Task, Datasets and Supervised Baseline
Ori Ernst, Ori Shapira, Ramakanth Pasunuru, Michael Lepioshkin, Jacob Goldberger, Mohit Bansal, Ido Dagan, 2021. [PDF](https://arxiv.org/pdf/2009.00590)

**How to use?**

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("biu-nlp/superpal")

model = AutoModelForSequenceClassification.from_pretrained("biu-nlp/superpal")
```



The original repo is [here](https://github.com/oriern/SuperPAL).


If you find our work useful, please cite the paper as:

```python
@misc{ernst2021summarysource,
      title={Summary-Source Proposition-level Alignment: Task, Datasets and Supervised Baseline}, 
      author={Ori Ernst and Ori Shapira and Ramakanth Pasunuru and Michael Lepioshkin and Jacob Goldberger and Mohit Bansal and Ido Dagan},
      year={2021},
      eprint={2009.00590},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```