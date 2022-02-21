---
language: si
tags:
- Sinhala
- text-generation
- gpt2
datasets:
- mc4
---
### Overview

This is a smaller GPT2 model trained on [MC4](https://github.com/allenai/allennlp/discussions/5056) Sinhala dataset. As Sinhala is one of those low resource languages, there are only a handful of models been trained. So, this would be a great place to start training for more downstream tasks. 

## Model Specification


The model chosen for training is GPT2 with the following specifications:
 1. vocab_size=50257
 2. n_embd=768
 3. n_head=12
 4. n_layer=12
 5. n_positions=1024
 
## How to Use
You can use this model directly with a pipeline for casual language modeling:

```py
from transformers import pipeline
generator = pipeline('text-generation', model='keshan/sinhala-gpt2')
generator("මම", max_length=50, num_return_sequences=5)
```
