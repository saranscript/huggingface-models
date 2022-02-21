\n---
tags:
- Causal Language modeling
- text-generation
- CLM
model_index:
- name: MechDistilGPT2
  results:
  - task:
      name: Causal Language modeling
      type: Causal Language modeling
---
## MechDistilGPT2
This model is fine-tuned on text scraped from 100+ Mechanical/Automotive pdf books.

Base model is DistilGPT2(https://huggingface.co/gpt2) (the smallest version of GPT2)

## Fine-Tuning
* Default Training Args
* Epochs = 3
* Training set = 200k sentences
* Validation set = 40k sentences

## Framework versions
* Transformers 4.7.0.dev0
* Pytorch 1.8.1+cu111
* Datasets 1.6.2
* Tokenizers 0.10.2

## References
https://github.com/huggingface/notebooks/blob/master/examples/language_modeling.ipynb