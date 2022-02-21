---
language: en
tags:
- bart
- question
- generation
- seq2seq
datasets:
- unifiedQA
metrics:
- bleu
- rouge
pipeline_tag: text2text-generation
widget:
- text: "Harry Potter is a series of seven fantasy novels written by British author J. K. Rowling. The novels chronicle the lives of a young wizard, Harry Potter, and his friends Hermione Granger and Ron Weasley, all of whom are students at Hogwarts School of Witchcraft and Wizardry. The main story arc concerns Harry's struggle against Lord Voldemort, a dark wizard who intends to become immortal, overthrow the wizard governing body known as the Ministry of Magic and subjugate all wizards and Muggles(non-magical people)."
---
# context-only-question-generator

## Model description

This model is a sequence-to-sequence question generator which takes context as an input, and generates a question as an output.   
It is based on a pretrained `bart-base` model.     

#### How to use

Inputs should be organised into the following format:   
```
context 
```
The input sequence can then be encoded and passed as the `input_ids` argument in the model's `generate()` method.
