---
language:
- en
tags:
- text generation
- pytorch
- causal-lm
license: apache-2.0
datasets:
- custom
---

# GPT-Neo 125M finetuned with beer recipes

## Model Description

GPT-Neo 125M is a transformer model based on EleutherAI's replication of the GPT-3 architecture https://huggingface.co/EleutherAI/gpt-neo-125M.
It generates recipes for brewing beer in a YAML-like format which can be easily used for different purposes.

Is it useful? Not sure - but it was really fun to create it :laughing:

## Training data

This model was trained on a custom dataset of ~ 76,800 beer recipes from the internet. It includes recipes for the following 
styles of beer:

* Strong American Ale 
* Pale American Ale
* India Pale Ale (IPA)
* Standard American Beer
* Stout
* English Pale Ale
* IPA
* American Porter and Stout
* Sour Ale
* Irish Beer
* Strong British Ale
* Belgian and French Ale
* German Wheat and Rye Beer
* Czech Lager
* Spice/Herb/Vegetable Beer
* Specialty Beer
* American Ale
* Pilsner
* Belgian Ale
* Strong Belgian Ale
* Bock
* Brown British Beer
* German Wheat Beer
* Fruit Beer
* Amber Malty European Lager
* Pale Malty European Lager
* British Bitter
* Amber and Brown American Beer
* Light Hybrid Beer
* Pale Commonwealth Beer
* American Wild Ale
* European Amber Lager
* Belgian Strong Ale
* International Lager
* Amber Bitter European Lager
* Light Lager
* Scottish and Irish Ale
* European Sour Ale
* Trappist Ale
* Strong European Beer
* Porter
* Historical Beer
* Pale Bitter European Beer
* Amber Hybrid Beer
* Smoke Flavored/Wood-Aged Beer
* Spiced Beer
* Dark European Lager
* Alternative Fermentables Beer
* Mead
* Strong Ale
* Dark British Beer
* Scottish Ale
* Smoked Beer
* English Brown Ale
* Dark Lager
* Cider or Perry
* Wood Beer

### How to use

You can use this model directly with a pipeline for text generation. This example generates a different recipe each time it's run:

```py
>>> from transformers import pipeline
>>> generator = pipeline('text-generation', model='b3ck1/gpt-neo-125M-finetuned-beer-recipes')
>>> generator("style: Pilsner\nbatch_size: 20\nefficiency: 75\nboil_size:", do_sample=True, min_length=50, max_length=500)
>>> print(output[0]['generated_text'])

style: Pilsner
batch_size: 20
efficiency: 70
boil_size: 24
boil_time: 60
fermentables:
- name: Pale Ale
  type: Grain
  amount: 6.5
hops:
- name: Saaz
  alpha: 3.5
  use: Boil
  time: 60
  amount: 0.06
- name: Saaz
  alpha: 3.5
  use: Boil
  time: 30
  amount: 0.06
- name: Saaz
  alpha: 3.5
  use: Boil
  time: 10
  amount: 0.06
- name: Saaz
  alpha: 3.5
  use: Boil
  time: 0
  amount: 0.06
yeasts:
- name: Safale - American Ale Yeast US-05
  amount: 0.11
  min_temperature: 12
  max_temperature: 25
primary_temp: null
mash_steps:
- step_temp: 65
  step_time: 60
miscs: []
```

### See this model in action

This model was used to build https://beerai.net.