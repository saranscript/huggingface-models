---
language: en
tags:
- bart
- question
- generation
- seq2seq
datasets:
- eqg-race
metrics:
- bleu
- rouge
pipeline_tag: text2text-generation
widget:
- text: "When you ' re having a holiday , one of the main questions to ask is which hotel or apartment to choose . However , when it comes to France , you have another special choice : treehouses . In France , treehouses are offered to travelers as a new choice in many places . The price may be a little higher , but you do have a chance to _ your childhood memories . Alain Laurens , one of France ' s top treehouse designers , said , ' Most of the people might have the experience of building a den when they were young . And they like that feeling of freedom when they are children . ' Its fairy - tale style gives travelers a special feeling . It seems as if they are living as a forest king and enjoying the fresh air in the morning . Another kind of treehouse is the ' star cube ' . It gives travelers the chance of looking at the stars shining in the sky when they are going to sleep . Each ' star cube ' not only offers all the comfortable things that a hotel provides for travelers , but also gives them a chance to look for stars by using a telescope . The glass roof allows you to look at the stars from your bed . "
---
# voidful/bart-eqg-question-generator

## Model description

This model is a sequence-to-sequence question generator with only the context as an input, and generates a  question as an output.      
It is based on a pretrained `bart-base` model, and trained on [EQG-RACE](https://github.com/jemmryx/EQG-RACE) corpus.      

## Intended uses & limitations

The model is trained to generate examinations-style multiple choice question.

#### How to use

The model takes context as an input sequence, and will generate a question as an output sequence. The max sequence length is 1024 tokens. Inputs should be organised into the following format:
```
context
```
The input sequence can then be encoded and passed as the `input_ids` argument in the model's `generate()` method.
