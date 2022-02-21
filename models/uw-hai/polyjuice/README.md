---
language: "en"
tags:
- counterfactual generation
widget:
- text: "It is great for kids. <|perturb|> [negation] It [BLANK] great for kids. [SEP]"
---

# Polyjuice

## Model description

This is a ported version of [Polyjuice](https://homes.cs.washington.edu/~wtshuang/static/papers/2021-arxiv-polyjuice.pdf), the general-purpose counterfactual generator.
For more code release, please refer to [this github page](https://github.com/tongshuangwu/polyjuice).

#### How to use

```python
from transformers import AutoTokenizer, AutoModelWithLMHead
from transformers import pipeline, AutoTokenizer, AutoModelForCausalLM

model_path = "uw-hai/polyjuice"
generator = pipeline("text-generation", 
    model=AutoModelForCausalLM.from_pretrained(model_path), 
    tokenizer=AutoTokenizer.from_pretrained(model_path),
    framework="pt", device=0 if is_cuda else -1)

prompt_text = "A dog is embraced by the woman. <|perturb|> [negation] A dog is [BLANK] the woman."
generator(prompt_text, num_beams=3, num_return_sequences=3)
```

### BibTeX entry and citation info

```bibtex
@inproceedings{polyjuice:acl21,
    title = "{P}olyjuice: Generating Counterfactuals for Explaining, Evaluating, and Improving Models",
    author = "Tongshuang Wu and Marco Tulio Ribeiro and Jeffrey Heer and Daniel S. Weld",
    booktitle = "Proceedings of the 59th Annual Meeting of the Association for Computational Linguistics",
    year = "2021",
    publisher = "Association for Computational Linguistics"
```