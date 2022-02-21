---
language:
- gr
thumbnail: https://huggingface.co/macedonizer/gr-roberta-base/lets-talk-about-nlp-gr.jpg
tags:
- masked-lm
license: apache-2.0
datasets:
- wiki-gr
---

# GR-RoBERTa base model
Pretrained model on Macedonian language using a masked language modeling (MLM) objective. It was introduced in this paper and first released in this repository. This model is case-sensitive: it makes a difference between Athens and athens.

# Model description
RoBERTa is a transformers model pre-trained on a large corpus of мацед data in a self-supervised fashion. This means it was pre-trained on the raw texts only, with no humans labeling them in any way (which is why it can use lots of publicly available data) with an automatic process to generate inputs and labels from those texts.

More precisely, it was pre-trained with the Masked language modeling (MLM) objective. Taking a sentence, the model randomly masks 15% of the words in the input then runs the entire masked sentence through the model and has to predict the masked words. This is different from traditional recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like GPT which internally mask the future tokens. It allows the model to learn a bidirectional representation of the sentence.

This way, the model learns an inner representation of the Greek language that can then be used to extract features useful for downstream tasks: if you have a dataset of labeled sentences, for instance, you can train a standard classifier using the features produced by the BERT model as inputs.

# Intended uses & limitations
You can use the raw model for masked language modeling, but it's mostly intended to be fine-tuned on a downstream task. See the model hub to look for fine-tuned versions of a task that interests you.
Note that this model is primarily aimed at being fine-tuned on tasks that use the whole sentence (potentially masked) to make decisions, such as sequence classification, token classification, or question answering. For tasks such as text generation, you should look at models like GPT2.

# How to use
You can use this model directly with a pipeline for masked language modeling:

from transformers import pipeline \
unmasker = pipeline('fill-mask', model='macedonizer/gr-roberta-base') \
unmasker("Η Αθήνα είναι η \<mask\> της Ελλάδας") \

[{'score': 0.8832866549491882, \
  'sequence': 'Η Αθήνα είναι η πρωτεύουσα της Ελλάδας', \
  'token': 2788, \
  'token_str': ' πρωτεύουσα'}, \
 {'score': 0.018105432391166687, \
  'sequence': 'Η Αθήνα είναι η μεγαλύτερη της Ελλάδας', \
  'token': 2363, \
  'token_str': ' μεγαλύτερη'}, \
 {'score': 0.015836946666240692, \
  'sequence': 'Η Αθήνα είναι η έδρα της Ελλάδας', \
  'token': 1950, \
  'token_str': ' έδρα'}, \
 {'score': 0.015673324465751648, \
  'sequence': 'Η Αθήνα είναι η μόνη της Ελλάδας', \
  'token': 6548, \
  'token_str': ' μόνη'}, \
 {'score': 0.01375910360366106, \
  'sequence': 'Η Αθήνα είναι η πόλη της Ελλάδας', \
  'token': 825, \
  'token_str': ' πόλη'}]

Here is how to use this model to get the features of a given text in PyTorch:

from transformers import RobertaTokenizer, RobertaModel \
tokenizer = RobertaTokenizer.from_pretrained('macedonizer/gr-roberta-base') \
model = RobertaModel.from_pretrained('macedonizer/gr-roberta-base') \
text = "Replace me by any text you'd like." \
encoded_input = tokenizer(text, return_tensors='pt') \
output = model(**encoded_input)