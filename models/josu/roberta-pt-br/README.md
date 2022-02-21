---
language: pt
tags:
- portuguese
- brazil
- pt_BR
widget:
- text: Brasilia é a capital do <mask>
---

``` python
from transformers import pipeline
unmasker = pipeline('fill-mask', model='josu/roberta-pt-br')
text = 'Brasilia é a capital do <mask>'


[{'sequence': 'Brasilia é a capital do Brasil',
  'score': 0.24386335909366608,
  'token': 707,
  'token_str': ' Brasil'},
 {'sequence': 'Brasilia é a capital do estado',
  'score': 0.2320091277360916,
  'token': 1031,
  'token_str': ' estado'},
 {'sequence': 'Brasilia é a capital do país',
  'score': 0.0665697380900383,
  'token': 998,
  'token_str': ' país'},
 {'sequence': 'Brasilia é a capital do Rio',
  'score': 0.05980581417679787,
  'token': 993,
  'token_str': ' Rio'},
 {'sequence': 'Brasilia é a capital do capital',
  'score': 0.058453518897295,
  'token': 2027,
  'token_str': ' capital'}]
  
  ```
