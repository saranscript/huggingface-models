---
language: 
- en
datasets:
- c4
- squad
tags:
- text2text-generation
widget:
- text: "question: What is the atomic number for oxygen? context: Oxygen is a chemical element with symbol O and atomic number 8."
- text: "question: What is the chemical symbol of Oxygen? context: Oxygen is a chemical element with symbol O and atomic number 8."

license: apache-2.0
---


T5-small for QA
---

[Google's T5-small](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) pre-trained on the [C4](https://huggingface.co/datasets/c4) dataset, fine-tuned for Question-Answering on [SQuAD v2](https://huggingface.co/datasets/squad_v2) with the following hyperparameters:

```
  optimizer=adamw_hf
  learning_rate=3e-5
  adam_beta1=0.9
  adam_beta2=0.999
  adam_epsilon=1e-08
  num_train_epochs=2
  per_device_train_batch_size=12
```


Usage
---

The input [context and question] has to be prepared in a specific way as follows:

```python
from transformers import pipeline

def prep_input(_context, _question):
    return " ".join(["question:", _question.strip(), "context:", _context.strip()])

t5qa = pipeline("text2text-generation", "fgaim/t5-small-squad-v2")

context = """
Oxygen is a chemical element with symbol O and atomic number 8. It is a member of the chalcogen group on the periodic table and is a highly reactive nonmetal and oxidizing agent that readily forms compounds (notably oxides) with most elements. By mass, oxygen is the third-most abundant element in the universe, after hydrogen and helium. At standard temperature and pressure, two atoms of the element bind to form dioxygen, a colorless and odorless diatomic gas with the formula O.
"""

t5qa(prep_input(context, "How many atoms combine to form dioxygen?"))
# [{'generated_text': 'two'}]

t5qa(prep_input(context, "What element makes up almost half of the earth's crust by mass?"))
# [{'generated_text': 'oxygen'}]

t5qa(prep_input(context, "What are the most abundent elements of the universe by mass?"))
# [{'generated_text': 'hydrogen and helium'}]
```
