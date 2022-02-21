---
license: apache-2.0
tags:
- generated_from_trainer
- gpt-neo
- borat
- cash-money
- memes
dataset:
- mysterious
widget:
- text: "I hope you"  
  example_title: "rodeo"
- text: "My name Borat! I want"  
  example_title: "my name"
- text: "BORAT: how can I"
  example_title: "question"
- text: "my wife is"
  example_title: "wife"
- text: "BORAT: very nice"
  example_title: "very nice"
- text: "American wine is like"  
  example_title: "wine"
inference:
  parameters:
    min_length: 2
    max_length: 64
    length_penalty: 0.6
    no_repeat_ngram_size: 3
    do_sample: True
    top_p: 0.90
    top_k: 30
    repetition_penalty: 5.2
    
---

# GPT-Neo: Borat (tiny)

This model is a fine-tuned version of [EleutherAI/gpt-neo-125M](https://huggingface.co/EleutherAI/gpt-neo-125M) on a mysterious dataset.
It achieves the following results on the evaluation set:
- Loss: 5.1797

---

# Usage in Python

- install packages if needed
```
pip install -U transformers 
```
- use in python codes for make benefit of kazakhstan:

```
from transformers import pipeline

text_generator = pipeline("text-generation", "pszemraj/gpt-neo-tiny-borat")
result = text_generator(
            "America national sport is called baseballs. Today I", 
            max_length=128, 
            do_sample=True
          )
          
print(result)

```

---

# About

## Intended uses & limitations

- GLORY TO KAZAKHSTAN

## Training and evaluation data

- GLORIOUS

## Training procedure

- IS VERY NICE!!

### Training hyperparameters

The following hyperparameters were used during training:

- learning_rate: 4e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- num_epochs: 50

### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Tokenizers 0.11.0
