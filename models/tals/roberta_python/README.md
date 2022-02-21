# roberta_python
---
language: python
datasets:
- code_search_net
- Fraser/python-lines
tags:
- python
- code
- masked-lm
widget:
- text "assert 6 == sum([i for i in range(<mask>)])"
---
# Details
This is a roBERTa-base model trained on the python part of [CodeSearchNet](https://github.com/github/CodeSearchNet) and reached a dev perplexity of 3.296

This model was used for the Programming Puzzles enumerative solver baseline detailed in [Programming Puzzles paper](https://arxiv.org/abs/2106.05784).

See also the [Python Programming Puzzles (P3) Repository](https://github.com/microsoft/PythonProgrammingPuzzles) for more details.

# Usage

You can either load the model and further fine-tune it for a target task (as done for the puzzle solver), or you can experiment with mask-filling directly with this model as in the following example:

```python
from transformers import AutoTokenizer, AutoModelWithLMHead, pipeline

tokenizer = AutoTokenizer.from_pretrained("tals/roberta_python")
model = AutoModelWithLMHead.from_pretrained("tals/roberta_python")

demo = pipeline("fill-mask", model=model, tokenizer=tokenizer)

code = """sum= 0
for i in range(<mask>):
    sum += i
assert sum == 6
"""
demo(code)
```

# BibTeX entry and citation info

```bibtex
@article{schuster2021programming,
      title={Programming Puzzles}, 
      author={Tal Schuster and Ashwin Kalyan and Oleksandr Polozov and Adam Tauman Kalai},
      year={2021},
      eprint={2106.05784},
      archivePrefix={arXiv},    
      url={https://arxiv.org/abs/2106.05784}  
}
```
