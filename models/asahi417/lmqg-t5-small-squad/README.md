---
language: en
tags:
- question generation
- question answer generation
license: cc-by-4.0
datasets:
- squad
- asahi417/qg_squad
metrics:
- bleu
- meteor
- rouge
widget:
- text: "generate question: <hl> Beyonce <hl> further expanded her acting career, starring as blues singer Etta James in the 2008 musical biopic, Cadillac Records."
  example_title: "Example 1"
- text: "generate question: Beyonce further expanded her acting career, starring as blues singer <hl> Etta James <hl> in the 2008 musical biopic, Cadillac Records."
  example_title: "Example 2"
- text: "generate question: Beyonce further expanded her acting career, starring as blues singer Etta James in the 2008 musical biopic,  <hl> Cadillac Records  <hl> ."
  example_title: "Example 3"
pipeline_tag: text2text-generation
---

# t5-small for question generation
T5 model for question generation. Please visit [our repository](https://github.com/asahi417/lm-question-generation) for more detail.

## Overview

**Language model:** t5-small   
**Language:** English (en)    
**Downstream-task:** Question Generation  
**Training data:** SQuAD  
**Eval data:** SQuAD   
**Code:**  See [our repository](https://github.com/asahi417/lm-question-generation)

## Usage
### In Transformers
```python
from transformers import pipeline

model_path = 'asahi417/lmqg-t5-small-squad'
pipe = pipeline("text2text-generation", model_path)

paragraph = 'Beyonce further expanded her acting career, starring as blues singer Etta James in the 2008 musical biopic, Cadillac Records.'
# highlight an answer in the paragraph to generate question
answer = 'Etta James'
highlight_token = '<hl>'
input_text = paragraph.replace(answer, '{0} {1} {0}'.format(highlight_token, answer))
# add task specifix prefix
input_text = 'generate question: {}'.format(input_text)
print(input_text)
>>> generate question: Beyonce further expanded her acting career, starring as blues singer <hl> Etta James <hl> in the 2008 musical biopic, Cadillac Records.
# model generation
generation = pipe(input_text)
print(generation)
>>> [{'generated_text': 'What is the name of the biopic that Beyonce starred in?'}]
```

## Performance
TBA


