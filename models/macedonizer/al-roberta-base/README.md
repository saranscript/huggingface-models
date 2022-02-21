---
language:
- al
thumbnail: https://huggingface.co/macedonizer/al-roberta-base/lets-talk-about-nlp-al.jpg
tags:
- masked-lm
license: apache-2.0
datasets:
- wiki-sh
---

# AL-RoBERTa base model
Pretrained model on Albanian language using a masked language modeling (MLM) objective. It was introduced in this paper and first released in this repository. This model is case-sensitive: it makes a difference between tirana and Tirana.

# Model description
RoBERTa is a transformers model pre-trained on a large corpus of text data in a self-supervised fashion. This means it was pre-trained on the raw texts only, with no humans labeling them in any way (which is why it can use lots of publicly available data) with an automatic process to generate inputs and labels from those texts.

More precisely, it was pre-trained with the Masked language modeling (MLM) objective. Taking a sentence, the model randomly masks 15% of the words in the input then runs the entire masked sentence through the model and has to predict the masked words. This is different from traditional recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like GPT which internally mask the future tokens. It allows the model to learn a bidirectional representation of the sentence.

This way, the model learns an inner representation of the English language that can then be used to extract features useful for downstream tasks: if you have a dataset of labeled sentences, for instance, you can train a standard classifier using the features produced by the BERT model as inputs.

# Intended uses & limitations
You can use the raw model for masked language modeling, but it's mostly intended to be fine-tuned on a downstream task. See the model hub to look for fine-tuned versions of a task that interests you.
Note that this model is primarily aimed at being fine-tuned on tasks that use the whole sentence (potentially masked) to make decisions, such as sequence classification, token classification, or question answering. For tasks such as text generation, you should look at models like GPT2.

# How to use
You can use this model directly with a pipeline for masked language modeling: \

from transformers import pipeline \
unmasker = pipeline('fill-mask', model='macedonizer/al-roberta-base') \
unmasker("Tirana është \\<mask\\> i Shqipërisë.") \

[{'score': 0.9426872134208679,
  'sequence': 'Tirana është kryeqyteti i Shqipërisë',
  'token': 7901,
  'token_str': ' kryeqyteti'},
 {'score': 0.03112833760678768,
  'sequence': 'Tirana është kryeqytet i Shqipërisë',
  'token': 7439,
  'token_str': ' kryeqytet'},
 {'score': 0.0022084848023951054,
  'sequence': 'Tirana është qytet i Shqipërisë',
  'token': 2246,
  'token_str': ' qytet'},
 {'score': 0.0016222079284489155,
  'sequence': 'Tirana është qyteti i Shqipërisë',
  'token': 2784,
  'token_str': ' qyteti'},
 {'score': 0.0008979254635050893,
  'sequence': 'Tirana është Kryeqytet i Shqipërisë',
  'token': 37653,
  'token_str': ' Kryeqytet'}]

Here is how to use this model to get the features of a given text in PyTorch:

from transformers import RobertaTokenizer, RobertaModel \
tokenizer = RobertaTokenizer.from_pretrained('macedonizer/al-roberta-base') \
model = RobertaModel.from_pretrained('macedonizer/al-roberta-base') \
text = "Replace me by any text you'd like." \
encoded_input = tokenizer(text, return_tensors='pt') \
output = model(**encoded_input)