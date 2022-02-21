---
language:
- sl
thumbnail: https://huggingface.co/macedonizer/mkgpt2/lets-talk-about-nlp.jpg
license: apache-2.0
datasets:
- wiki-sl
---

# sl-gpt2
Test the whole generation capabilities here: https://transformer.huggingface.co/doc/gpt2-large
Pretrained model on English language using a causal language modeling (CLM) objective. It was introduced in
[this paper](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)
and first released at [this page](https://openai.com/blog/better-language-models/).

## Model description
sl-gpt2 is a transformers model pretrained on a very large corpus of Slovenian data in a self-supervised fashion. This
means it was pretrained on the raw texts only, with no humans labelling them in any way (which is why it can use lots
of publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely,
it was trained to guess the next word in sentences.
More precisely, inputs are sequences of continuous text of a certain length and the targets are the same sequence,
shifted one token (word or piece of word) to the right. The model uses internally a mask-mechanism to make sure the
predictions for the token `i` only uses the inputs from `1` to `i` but not the future tokens.
This way, the model learns an inner representation of the Macedonian language that can then be used to extract features
useful for downstream tasks. The model is best at what it was pretrained for however, which is generating texts from a
prompt.

### How to use
Here is how to use this model to get the features of a given text in PyTorch:

import random
from transformers import AutoTokenizer, AutoModelWithLMHead

tokenizer = AutoTokenizer.from_pretrained('macedonizer/sl-gpt2') \
model = AutoModelWithLMHead.from_pretrained('macedonizer/sl-gpt2')

input_text = 'Ljubljana '

if len(input_text) == 0: \
    encoded_input = tokenizer(input_text, return_tensors="pt") \
    output = model.generate( \
        bos_token_id=random.randint(1, 50000), \
        do_sample=True, \
        top_k=50, \
        max_length=1024, \
        top_p=0.95, \
        num_return_sequences=1, \
    ) \
else: \
    encoded_input = tokenizer(input_text, return_tensors="pt") \
    output = model.generate( \
        **encoded_input, \
        bos_token_id=random.randint(1, 50000), \
        do_sample=True, \
        top_k=50, \
        max_length=1024, \
        top_p=0.95, \
        num_return_sequences=1, \
    )

decoded_output = [] \\nfor sample in output: \
    decoded_output.append(tokenizer.decode(sample, skip_special_tokens=True))

print(decoded_output)