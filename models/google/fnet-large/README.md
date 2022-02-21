---
language: en
tags:
- fnet
license: apache-2.0
datasets:
- c4
---

# FNet large model

Pretrained model on English language using a masked language modeling (MLM) and next sentence prediction (NSP) objective. It was 
introduced in [this paper](https://arxiv.org/abs/2105.03824) and first released in [this repository](https://github.com/google-research/google-research/tree/master/f_net).
This model is cased: it makes a difference between english and English. The model achieves 0.58 accuracy on MLM objective and 0.80 on NSP objective.

Disclaimer: This model card has been written by [gchhablani](https://huggingface.co/gchhablani).

## Model description

FNet is a transformers model with attention replaced with fourier transforms. Hence, the inputs do not contain an `attention_mask`. It is pretrained on a large corpus of 
English data in a self-supervised fashion. This means it was pretrained on the raw texts only, with no humans labelling
them in any way (which is why it can use lots of publicly available data) with an automatic process to generate inputs and 
labels from those texts. More precisely, it was pretrained with two objectives:

- Masked language modeling (MLM): taking a sentence, the model randomly masks 15% of the words in the input then run
  the entire masked sentence through the model and has to predict the masked words. This is different from traditional
  recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like
  GPT which internally mask the future tokens. It allows the model to learn a bidirectional representation of the
  sentence.
- Next sentence prediction (NSP): the models concatenates two masked sentences as inputs during pretraining. Sometimes
  they correspond to sentences that were next to each other in the original text, sometimes not. The model then has to
  predict if the two sentences were following each other or not.

This way, the model learns an inner representation of the English language that can then be used to extract features
useful for downstream tasks: if you have a dataset of labeled sentences for instance, you can train a standard
classifier using the features produced by the FNet model as inputs.

This model has the following configuration:
- 24-layer
- 1024 hidden dimension

## Intended uses & limitations

You can use the raw model for either masked language modeling or next sentence prediction, but it's mostly intended to
be fine-tuned on a downstream task. See the [model hub](https://huggingface.co/models?filter=fnet) to look for
fine-tuned versions on a task that interests you.

Note that this model is primarily aimed at being fine-tuned on tasks that use the whole sentence (potentially masked)
to make decisions, such as sequence classification, token classification or question answering. For tasks such as text
generation you should look at model like GPT2.

### How to use

You can use this model directly with a pipeline for masked language modeling:

**Note: The mask filling pipeline doesn't work exactly as the original model performs masking after converting to tokens. In masking pipeline an additional space is added after the [MASK].**

```python
>>> from transformers import FNetForMaskedLM, FNetTokenizer, pipeline
>>> tokenizer = FNetTokenizer.from_pretrained("google/fnet-large")
>>> model = FNetForMaskedLM.from_pretrained("google/fnet-large")
>>> unmasker = pipeline('fill-mask', model=model, tokenizer=tokenizer)
>>> unmasker("Hello I'm a [MASK] model.")

[
    {"sequence": "hello i'm a. model.", "score": 0.12840192019939423, "token": 16678, "token_str": "."},
    {"sequence": "hello i'm a a model.", "score": 0.07460460811853409, "token": 8, "token_str": "a"},
    {"sequence": "hello i'm a, model.", "score": 0.05011311173439026, "token": 16680, "token_str": ","},
    {"sequence": "hello i'm a and model.", "score": 0.047409165650606155, "token": 36, "token_str": "and"},
    {"sequence": "hello i'm a the model.", "score": 0.0269990973174572, "token": 13, "token_str": "the"},
]

```

Here is how to use this model to get the features of a given text in PyTorch:

**Note: You must specify the maximum sequence length to be 512 and truncate/pad to the same length because the original model has no attention mask and considers all the hidden states during forward pass.**

```python
from transformers import FNetTokenizer, FNetModel
tokenizer = FNetTokenizer.from_pretrained("google/fnet-large")
model = FNetModel.from_pretrained("google/fnet-large")
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='pt', padding='max_length', truncation=True, max_length=512)
output = model(**encoded_input)
```

### Limitations and bias

Even if the training data used for this model could be characterized as fairly neutral, this model can have biased predictions. However, the model's MLM accuracy may also affect answers. Given below are some example where gender-bias could be expected:

```python
>>> from transformers import FNetForMaskedLM, FNetTokenizer, pipeline
>>> tokenizer = FNetTokenizer.from_pretrained("google/fnet-large")
>>> model = FNetForMaskedLM.from_pretrained("google/fnet-large")
>>> unmasker = pipeline('fill-mask', model=model, tokenizer=tokenizer)
>>> unmasker("The man worked as a [MASK].")

[
    {"sequence": "the man worked as a a.", "score": 0.39862048625946045, "token": 8, "token_str": "a"},
    {"sequence": "the man worked as a the.", "score": 0.20786496996879578, "token": 13, "token_str": "the"},
    {"sequence": "the man worked as a as.", "score": 0.012523212470114231, "token": 106, "token_str": "as"},
    {"sequence": "the man worked as a an.", "score": 0.010838045738637447, "token": 102, "token_str": "an"},
    {"sequence": "the man worked as a and.", "score": 0.006571347825229168, "token": 36, "token_str": "and"},
]

>>> unmasker("The woman worked as a [MASK].")

[
    {"sequence": "the woman worked as a the.", "score": 0.3320266902446747, "token": 13, "token_str": "the"},
    {"sequence": "the woman worked as a a.", "score": 0.2591220438480377, "token": 8, "token_str": "a"},
    {"sequence": "the woman worked as a as.", "score": 0.011250585317611694, "token": 106, "token_str": "as"},
    {"sequence": "the woman worked as a an.", "score": 0.010153685696423054, "token": 102, "token_str": "an"},
    {"sequence": "the woman worked as a and.", "score": 0.010126154869794846, "token": 36, "token_str": "and"},
]
```

This bias will also affect all fine-tuned versions of this model.

## Training data

The FNet model was pretrained on [C4](https://huggingface.co/datasets/c4), a cleaned version of the Common Crawl dataset.

## Training procedure

### Preprocessing

The texts are lowercased and tokenized using SentencePiece and a vocabulary size of 32,000. The inputs of the model are
then of the form:

```
[CLS] Sentence A [SEP] Sentence B [SEP]
```

With probability 0.5, sentence A and sentence B correspond to two consecutive sentences in the original corpus and in
the other cases, it's another random sentence in the corpus. Note that what is considered a sentence here is a
consecutive span of text usually longer than a single sentence. The only constrain is that the result with the two
"sentences" has a combined length of less than 512 tokens.

The details of the masking procedure for each sentence are the following:
- 15% of the tokens are masked.
- In 80% of the cases, the masked tokens are replaced by `[MASK]`.
- In 10% of the cases, the masked tokens are replaced by a random token (different) from the one they replace.
- In the 10% remaining cases, the masked tokens are left as is.

### Pretraining

The model was trained on 4 cloud TPUs in Pod configuration (16 TPU chips total) for one million steps with a batch size
of 256. The sequence length was limited to 512 tokens. The optimizer
used is Adam with a learning rate of 1e-4, \\(\beta_{1} = 0.9\\) and \\(\beta_{2} = 0.999\\), a weight decay of 0.01,
learning rate warmup for 10,000 steps and linear decay of the learning rate after.

## Evaluation results

When fine-tuned on downstream tasks, this model achieves the following results:

Glue test results:

| Task | MNLI-(m/mm) | QQP  | QNLI | SST-2 | CoLA | STS-B | MRPC | RTE  | Average |
|:----:|:-----------:|:----:|:----:|:-----:|:----:|:-----:|:----:|:----:|:-------:|
|      | 78/76   | 85 | 85 | 94  | 78 | 84  | 88 | 69| 81.9    |


### BibTeX entry and citation info

```bibtex
@article{DBLP:journals/corr/abs-2105-03824,
  author    = {James Lee{-}Thorp and
               Joshua Ainslie and
               Ilya Eckstein and
               Santiago Onta{\~{n}}{\'{o}}n},
  title     = {FNet: Mixing Tokens with Fourier Transforms},
  journal   = {CoRR},
  volume    = {abs/2105.03824},
  year      = {2021},
  url       = {https://arxiv.org/abs/2105.03824},
  archivePrefix = {arXiv},
  eprint    = {2105.03824},
  timestamp = {Fri, 14 May 2021 12:13:30 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2105-03824.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

## Contributions
Thanks to [@gchhablani](https://huggingface.co/gchhablani) for adding this model.