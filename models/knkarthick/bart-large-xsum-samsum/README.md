---
language: en
tags:
- bart
- seq2seq
- summarization
license: apache-2.0
datasets:
- samsum
widget:
- text: | 
    Hannah: Hey, do you have Betty's number?
    Amanda: Lemme check
    Amanda: Sorry, can't find it.
    Amanda: Ask Larry
    Amanda: He called her last time we were at the park together
    Hannah: I don't know him well
    Amanda: Don't be shy, he's very nice
    Hannah: If you say so..
    Hannah: I'd rather you texted him
    Amanda: Just text him 🙂
    Hannah: Urgh.. Alright
    Hannah: Bye
    Amanda: Bye bye
model-index:
- name: bart-large-xsum-samsum
  results:
  - task: 
      name: Abstractive Text Summarization
      type: abstractive-text-summarization
    dataset:
      name: "SAMSum Corpus: A Human-annotated Dialogue Dataset for Abstractive Summarization" 
      type: samsum
    metrics:
       - name: Validation ROGUE-1
         type: rogue-1
         value: 54.3921
       - name: Validation ROGUE-2
         type: rogue-2
         value: 29.8078
       - name: Validation ROGUE-L
         type: rogue-l
         value: 45.1543
       - name: Test ROGUE-1
         type: rogue-1
         value: 53.3059
       - name: Test ROGUE-2
         type: rogue-2
         value: 28.355
       - name: Test ROGUE-L
         type: rogue-l
         value: 44.0953 
---
## `bart-large-xsum-samsum`
This model was obtained by fine-tuning `facebook/bart-large-xsum` on [Samsum](https://huggingface.co/datasets/samsum) dataset.
## Usage
```python
from transformers import pipeline
summarizer = pipeline("summarization", model="knkarthick/bart-large-xsum-samsum")
conversation = '''Hannah: Hey, do you have Betty's number?
Amanda: Lemme check
Amanda: Sorry, can't find it.
Amanda: Ask Larry
Amanda: He called her last time we were at the park together
Hannah: I don't know him well
Amanda: Don't be shy, he's very nice
Hannah: If you say so..
Hannah: I'd rather you texted him
Amanda: Just text him 🙂
Hannah: Urgh.. Alright
Hannah: Bye
Amanda: Bye bye                                       
'''
summarizer(conversation)
```