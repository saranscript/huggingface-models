---
language: 
  - tg
widget:
- text: "Пойтахти <mask> Душанбе"
- text: "<mask> ба ин сайти шумо медароям."
- text: "Номи ман Акрам <mask>"

tags:
- generated_from_trainer
model_index:
- name: TajBERTo
  results:
  - task:
      name: Masked Language Modeling
      type: fill-mask
---

# TajBERTo: RoBERTa-like Language model trained on Tajik 
## First ever Tajik NLP model 🔥



# Dataset:
# This model was trained on filtered and merged version of Leipzig Corpora https://wortschatz.unileipzig.de/en/download/Tajik 

## Intended use 
# You can use the raw model for masked text generation or fine-tune it to a downstream task. 


## Example pipeline
```python
from transformers import pipeline
fill_mask = pipeline(
    "fill-mask",
    model="muhtasham/TajBERTo",
    tokenizer="muhtasham/TajBERTo"
)
fill_mask("Пойтахти <mask> Душанбе")

# This is the beginning of a beautiful <mask>.

{'score': 0.1952248513698578,
  'sequence': 'Пойтахти шаҳри Душанбе',
  'token': 710,
  'token_str': ' шаҳри'},
 {'score': 0.029092855751514435,
  'sequence': 'Пойтахти дар Душанбе',
  'token': 310,
  'token_str': ' дар'},
 {'score': 0.020065447315573692,
  'sequence': 'Пойтахти Душанбе Душанбе',
  'token': 717,
  'token_str': ' Душанбе'},
 {'score': 0.016725927591323853,
  'sequence': 'Пойтахти Тоҷикистон Душанбе',
  'token': 424,
  'token_str': ' Тоҷикистон'},
 {'score': 0.011400512419641018,
  'sequence': 'Пойтахти аз Душанбе',
  'token': 335,
  'token_str': ' аз'}
  
```


 