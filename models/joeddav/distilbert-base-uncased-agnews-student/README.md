---
language: en
tags:
- text-classification
- pytorch
- tensorflow
datasets:
- ag_news
license: mit
widget:
- text: "Armed conflict has been a near-constant policial and economic burden."
- text: "Tom Brady won his seventh Super Bowl last night."
- text: "Dow falls more than 100 points after disappointing jobs data"
- text: "A new moon has been discovered in Jupter's orbit."
---

# distilbert-base-uncased-agnews-student

## Model Description

This model is distilled from the zero-shot classification pipeline on the unlabeled AG's News dataset using [this
script](https://github.com/huggingface/transformers/tree/master/examples/research_projects/zero-shot-distillation).
It is the result of the demo notebook
[here](https://colab.research.google.com/drive/1mjBjd0cR8G57ZpsnFCS3ngGyo5nCa9ya?usp=sharing), where more details
about the model can be found.

- Teacher model: [roberta-large-mnli](https://huggingface.co/roberta-large-mnli)
- Teacher hypothesis template: `"This text is about {}."`

## Intended Usage

The model can be used like any other model trained on AG's News, but will likely not perform as well as a model
trained with full supervision. It is primarily intended as a demo of how an expensive NLI-based zero-shot model
can be distilled to a more efficient student.
