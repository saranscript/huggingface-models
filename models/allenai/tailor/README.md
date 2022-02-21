---
language: "en"
tags:
- controlled generation
- perturbation
widget:
- text: "[VERB+passive+past: break | PATIENT+partial: cup] <extra_id_0> <extra_id_1> <extra_id_2> ."
- max_length: 
---

# Tailor 

## Model description

This is a ported version of [Tailor](https://homes.cs.washington.edu/~wtshuang/static/papers/2021-arxiv-tailor.pdf), the general-purpose counterfactual generator.
For more code release, please refer to [this github page](https://github.com/allenai/tailor).

#### How to use

```python
from transformers import pipeline, AutoTokenizer, AutoModelForSeq2SeqLM

model_path = "allenai/tailor"
generator = pipeline("text2text-generation", 
    model=AutoModelForSeq2SeqLM.from_pretrained(model_path), 
    tokenizer=AutoTokenizer.from_pretrained(model_path),
    framework="pt", device=0)

prompt_text = "[VERB+active+past: comfort | AGENT+complete: the doctor | PATIENT+partial: athlete | LOCATIVE+partial: in] <extra_id_0> , <extra_id_1> <extra_id_2> <extra_id_3> ."
generator(prompt_text, max_length=200)
```
### BibTeX entry and citation info
```bibtex
@misc{ross2021tailor,
      title={Tailor: Generating and Perturbing Text with Semantic Controls}, 
      author={Alexis Ross and Tongshuang Wu and Hao Peng and Matthew E. Peters and Matt Gardner},
      year={2021},
      eprint={2107.07150},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2107.07150},
}
```
