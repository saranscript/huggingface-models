---
language: lt
tags:
- exbert
license: mit
---
# LitBERTa uncased model

Not the best model because of limited resources (Trained on ~4.7 GB of data on RTX2070 8GB for ~10 days) but it covers special lithuanian symbols `ąčęėįšųūž`. 128K vocabulary chosen because language has a lot of word forms.

## How to use
```python
from transformers import pipeline
unmasker = pipeline('fill-mask', model='jkeruotis/LitBERTa-uncased')
unmasker('lietuvių kalba yra viena iš <mask> kalbų pasaulyje.')
[{'sequence': 'lietuvių kalba yra viena iš populiariausių kalbų pasaulyje.',
  'score': 0.13887910544872284,
  'token': 9404,
  'token_str': ' populiariausių'},
 {'sequence': 'lietuvių kalba yra viena iš pirmaujančių kalbų pasaulyje.',
  'score': 0.13532795011997223,
  'token': 27431,
  'token_str': ' pirmaujančių'},
 {'sequence': 'lietuvių kalba yra viena iš seniausių kalbų pasaulyje.',
  'score': 0.1184583529829979,
  'token': 14775,
  'token_str': ' seniausių'},
 {'sequence': 'lietuvių kalba yra viena iš geriausių kalbų pasaulyje.',
  'score': 0.09306756407022476,
  'token': 5617,
  'token_str': ' geriausių'},
 {'sequence': 'lietuvių kalba yra viena iš nedaugelio kalbų pasaulyje.',
  'score': 0.08187634497880936,
  'token': 28150,
  'token_str': ' nedaugelio'}]```
