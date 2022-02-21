---
language: fr
license: apache-2.0
datasets:
- wikipedia
---

# FrALBERT Base

Pretrained model on French language using a masked language modeling (MLM) objective. It was introduced in
[this paper](https://arxiv.org/abs/1909.11942) and first released in
[this repository](https://github.com/google-research/albert). This model, as all ALBERT models, is uncased: it does not make a difference
between french and French.

## Model description

FrALBERT is a transformers model pretrained on 4Go of French Wikipedia in a self-supervised fashion. This means it
was pretrained on the raw texts only, with no humans labelling them in any way (which is why it can use lots of
publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely, it
was pretrained with two objectives:

- Masked language modeling (MLM): taking a sentence, the model randomly masks 15% of the words in the input then run
  the entire masked sentence through the model and has to predict the masked words. This is different from traditional
  recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like
  GPT which internally mask the future tokens. It allows the model to learn a bidirectional representation of the
  sentence.
- Sentence Ordering Prediction (SOP): FrALBERT uses a pretraining loss based on predicting the ordering of two consecutive segments of text.

This way, the model learns an inner representation of the English language that can then be used to extract features
useful for downstream tasks: if you have a dataset of labeled sentences for instance, you can train a standard
classifier using the features produced by the FrALBERT model as inputs.

FrALBERT is particular in that it shares its layers across its Transformer. Therefore, all layers have the same weights. Using repeating layers results in a small memory footprint, however, the computational cost remains similar to a BERT-like architecture with the same number of hidden layers as it has to iterate through the same number of (repeating) layers.

This is the first version of the base model. 

This model has the following configuration:

- 12 repeating layers
- 128 embedding dimension
- 768 hidden dimension
- 12 attention heads
- 11M parameters

## Intended uses & limitations

You can use the raw model for either masked language modeling or next sentence prediction, but it's mostly intended to
be fine-tuned on a downstream task. See the [model hub](https://huggingface.co/models?filter=fralbert) to look for
fine-tuned versions on a task that interests you.

Note that this model is primarily aimed at being fine-tuned on tasks that use the whole sentence (potentially masked)
to make decisions, such as sequence classification, token classification or question answering. For tasks such as text
generation you should look at model like GPT2.

### How to use

You can use this model directly with a pipeline for masked language modeling:

```python
>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='qwant/fralbert-base')
>>> unmasker("Paris est la capitale de la  [MASK] .")
[
  {
    "sequence": "paris est la capitale de la france.",
    "score": 0.6231236457824707,
    "token": 3043,
    "token_str": "france"
  },
  {
    "sequence": "paris est la capitale de la region.",
    "score": 0.2993471622467041,
    "token": 10531,
    "token_str": "region"
  },
  {
    "sequence": "paris est la capitale de la societe.",
    "score": 0.02028230018913746,
    "token": 24622,
    "token_str": "societe"
  },
  {
    "sequence": "paris est la capitale de la bretagne.",
    "score": 0.012089950032532215,
    "token": 24987,
    "token_str": "bretagne"
  },
  {
    "sequence": "paris est la capitale de la chine.",
    "score": 0.010002839379012585,
    "token": 14860,
    "token_str": "chine"
  }
]
```

Here is how to use this model to get the features of a given text in PyTorch:

```python
from transformers import AlbertTokenizer, AlbertModel
tokenizer = AlbertTokenizer.from_pretrained('qwant/fralbert-base')
model = AlbertModel.from_pretrained("qwant/fralbert-base")
text = "Remplacez-moi par le texte en français que vous souhaitez."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```

and in TensorFlow:

```python
from transformers import AlbertTokenizer, TFAlbertModel
tokenizer = AlbertTokenizer.from_pretrained('qwant/fralbert-base')
model = TFAlbertModel.from_pretrained("qwant/fralbert-base")
text = "Remplacez-moi par le texte en français que vous souhaitez."
encoded_input = tokenizer(text, return_tensors='tf')
output = model(encoded_input)
```


## Training data

The FrALBERT model was pretrained on 4go of [French Wikipedia](https://fr.wikipedia.org/wiki/French_Wikipedia) (excluding lists, tables and
headers).

## Training procedure

### Preprocessing

The texts are lowercased and tokenized using SentencePiece and a vocabulary size of 32,000. The inputs of the model are
then of the form:

```
[CLS] Sentence A [SEP] Sentence B [SEP]
```

### Training

The FrALBERT procedure follows the BERT setup.

The details of the masking procedure for each sentence are the following:
- 15% of the tokens are masked.
- In 80% of the cases, the masked tokens are replaced by `[MASK]`.
- In 10% of the cases, the masked tokens are replaced by a random token (different) from the one they replace.
- In the 10% remaining cases, the masked tokens are left as is.

## Evaluation results

When fine-tuned on downstream tasks, the ALBERT models achieve the following results:

|                | FQuAD1.0 | PIAF_dev 
|----------------|----------|----------
|frALBERT-base   |72.6/55.1 |61.0 / 38.9 


### BibTeX entry and citation info

```bibtex
@inproceedings{cattan2021fralbert,
  author    = {Oralie Cattan and
               Christophe Servan and
               Sophie Rosset},
  booktitle = {Recent Advances in Natural Language Processing, RANLP 2021},
  title     = {{On the Usability of Transformers-based models for a French Question-Answering task}},
  year      = {2021},
  address   = {Online},
  month     = sep,
}
```

Link to the paper: [PDF](https://hal.archives-ouvertes.fr/hal-03336060)
