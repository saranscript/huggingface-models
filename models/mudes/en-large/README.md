---
language: en
tags:
- mudes
license: apache-2.0
---

# MUDES - {Mu}ltilingual {De}tection of Offensive {S}pans

We provide state-of-the-art models to detect toxic spans in social media texts. We introduce our framework in [this paper](https://arxiv.org/abs/2102.09665). We have evaluated our models on Toxic Spans task at SemEval 2021 (Task 5). Our participation in the task is detailed in [this paper](https://arxiv.org/abs/2104.04630).


## Usage
You can use this model when you have [MUDES](https://github.com/TharinduDR/MUDES) installed:

```bash
pip install mudes
```

Then you can use the model like this:

```python
from mudes.app.mudes_app import MUDESApp

app = MUDESApp("en-large", use_cuda=False)
print(app.predict_toxic_spans("You motherfucking cunt", spans=True))

```

## System Demonstration
An experimental demonstration interface called MUDES-UI has been released on [GitHub](https://github.com/TharinduDR/MUDES-UI) and can be checked out in [here](http://rgcl.wlv.ac.uk/mudes/).


## Citing & Authors

If you find this model helpful, feel free to cite our publications

```bibtex
@inproceedings{ranasinghemudes,
 title={{MUDES: Multilingual Detection of Offensive Spans}}, 
 author={Tharindu Ranasinghe and Marcos Zampieri},  
 booktitle={Proceedings of NAACL},
 year={2021}
}
```

```bibtex
@inproceedings{ranasinghe2021semeval,
  title={{WLV-RIT at SemEval-2021 Task 5: A Neural Transformer Framework for Detecting Toxic Spans}},
  author = {Ranasinghe, Tharindu  and Sarkar, Diptanu and Zampieri, Marcos and Ororbia, Alex},
  booktitle={Proceedings of SemEval},
  year={2021}
}
```