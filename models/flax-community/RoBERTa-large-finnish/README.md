---
language:
- fi
license: apache-2.0
tags:
- finnish
- roberta
datasets:
- mc4
widget:
- text: "Moikka olen <mask> kielimalli."

---

# NOTE: We have trained newer and better Finnish RoBERTa large model which can be found from different repository: [https://huggingface.co/Finnish-NLP/roberta-large-finnish](https://huggingface.co/Finnish-NLP/roberta-large-finnish). Our future Finnish models will be available at the [Finnish-NLP](https://huggingface.co/Finnish-NLP) Hugging Face organization


# RoBERTa large model for Finnish

Pretrained model on Finnish language using a masked language modeling (MLM) objective. It was introduced in
[this paper](https://arxiv.org/abs/1907.11692) and first released in
[this repository](https://github.com/pytorch/fairseq/tree/master/examples/roberta). This model is case-sensitive: it
makes a difference between finnish and Finnish.

## Model description

RoBERTa is a transformers model pretrained on a large corpus of Finnish data in a self-supervised fashion. This means
it was pretrained on the raw texts only, with no humans labelling them in any way (which is why it can use lots of
publicly available data) with an automatic process to generate inputs and labels from those texts. 

More precisely, it was pretrained with the Masked language modeling (MLM) objective. Taking a sentence, the model
randomly masks 15% of the words in the input then run the entire masked sentence through the model and has to predict
the masked words. This is different from traditional recurrent neural networks (RNNs) that usually see the words one
after the other, or from autoregressive models like GPT which internally mask the future tokens. It allows the model to
learn a bidirectional representation of the sentence.

This way, the model learns an inner representation of the Finnish language that can then be used to extract features
useful for downstream tasks: if you have a dataset of labeled sentences for instance, you can train a standard
classifier using the features produced by the RoBERTa model as inputs.

## Intended uses & limitations

You can use the raw model for masked language modeling, but it's mostly intended to be fine-tuned on a downstream task.

Note that this model is primarily aimed at being fine-tuned on tasks that use the whole sentence (potentially masked)
to make decisions, such as sequence classification, token classification or question answering. For tasks such as text
generation you should look at model like GPT2.

### How to use

You can use this model directly with a pipeline for masked language modeling:

```python
>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='flax-community/RoBERTa-large-finnish')
>>> unmasker("Moikka olen <mask> kielimalli.")

[{'sequence': 'Moikka olen uusi kielimalli.',
  'score': 0.05129234120249748,
  'token': 1825,
  'token_str': ' uusi'},
 {'sequence': 'Moikka olen toinen kielimalli.',
  'score': 0.03112379088997841,
  'token': 2194,
  'token_str': ' toinen'},
 {'sequence': 'Moikka olen myös kielimalli.',
  'score': 0.025534993037581444,
  'token': 491,
  'token_str': ' myös'},
 {'sequence': 'Moikka olen ensimmäinen kielimalli.',
  'score': 0.020146571099758148,
  'token': 2832,
  'token_str': ' ensimmäinen'},
 {'sequence': 'Moikka olen vapaa kielimalli.',
  'score': 0.018089469522237778,
  'token': 2257,
  'token_str': ' vapaa'}]
```

Here is how to use this model to get the features of a given text in PyTorch:

```python
from transformers import RobertaTokenizer, RobertaModel
tokenizer = RobertaTokenizer.from_pretrained('flax-community/RoBERTa-large-finnish')
model = RobertaModel.from_pretrained('flax-community/RoBERTa-large-finnish')
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```

and in TensorFlow:

```python
from transformers import RobertaTokenizer, TFRobertaModel
tokenizer = RobertaTokenizer.from_pretrained('flax-community/RoBERTa-large-finnish')
model = TFRobertaModel.from_pretrained('flax-community/RoBERTa-large-finnish', from_pt=True)
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='tf')
output = model(encoded_input)
```

### Limitations and bias

The training data used for this model contains a lot of unfiltered content from the internet, which is far from
neutral. Therefore, the model can have biased predictions.

## Training data

This Finnish RoBERTa model was pretrained on the combination of two datasets:
- [mc4](https://huggingface.co/datasets/mc4), the dataset mC4 is a multilingual colossal, cleaned version of Common Crawl's web crawl corpus. We used the Finnish subset of the mC4 dataset
- [Yle Finnish News Archive](http://urn.fi/urn:nbn:fi:lb-2017070501)

Raw datasets were cleaned to filter out bad quality and non-Finnish examples. Together these cleaned datasets were around 51GB of text.

## Training procedure

### Preprocessing

The texts are tokenized using a byte version of Byte-Pair Encoding (BPE) and a vocabulary size of 50265. The inputs of
the model take pieces of 512 contiguous token that may span over documents. The beginning of a new document is marked
with `<s>` and the end of one by `</s>`

The details of the masking procedure for each sentence are the following:
- 15% of the tokens are masked.
- In 80% of the cases, the masked tokens are replaced by `<mask>`.

- In 10% of the cases, the masked tokens are replaced by a random token (different) from the one they replace.
- In the 10% remaining cases, the masked tokens are left as is.

Contrary to BERT, the masking is done dynamically during pretraining (e.g., it changes at each epoch and is not fixed).

### Pretraining

The model was trained on TPUv3-8 VM, sponsored by the Hugging Face JAX/Flax community week event, for 2 epochs with a sequence length of 128 and continuing for one more epoch with a sequence length of 512. The optimizer used is Adafactor with a learning rate of 2e-4, \\(\beta_{1} = 0.9\\), \\(\beta_{2} = 0.98\\) and \\(\epsilon = 1e-6\\), learning rate warmup for 1500 steps and linear decay of the learning rate after.

## Evaluation results

Evaluation was done by fine-tuning the model on downstream text classification task with two different labeled datasets: [Yle News](https://github.com/spyysalo/yle-corpus) and [Eduskunta](https://github.com/aajanki/eduskunta-vkk). Yle News classification fine-tuning was done with two different sequence lengths: 128 and 512 but Eduskunta only with 128 sequence length.
When fine-tuned on those datasets, this model (the first row of the table) achieves the following accuracy results compared to the [FinBERT (Finnish BERT)](https://huggingface.co/TurkuNLP/bert-base-finnish-cased-v1) and to our newer [Finnish RoBERTa-large](https://huggingface.co/Finnish-NLP/roberta-large-finnish) trained with larger dataset:

|                                        | Average  | Yle News 128 length | Yle News 512 length | Eduskunta 128 length |
|----------------------------------------|----------|---------------------|---------------------|----------------------|
|flax-community/RoBERTa-large-finnish    |87.72     |94.42                |95.06                |73.67                 |
|Finnish-NLP/roberta-large-finnish       |88.02     |94.53                |95.23                |74.30                 |
|TurkuNLP/bert-base-finnish-cased-v1     |**88.82** |**94.90**            |**95.49**            |**76.07**             |

To conclude, this model slightly loses to our newer [Finnish RoBERTa-large](https://huggingface.co/Finnish-NLP/roberta-large-finnish) model trained with larger dataset and also slightly loses to the [FinBERT (Finnish BERT)](https://huggingface.co/TurkuNLP/bert-base-finnish-cased-v1) model.

## Team Members

- Aapo Tanskanen, [Hugging Face profile](https://huggingface.co/aapot), [LinkedIn profile](https://www.linkedin.com/in/aapotanskanen/)
- Rasmus Toivanen [Hugging Face profile](https://huggingface.co/RASMUS), [LinkedIn profile](https://www.linkedin.com/in/rasmustoivanen/)
- Tommi Vehviläinen [Hugging Face profile](https://huggingface.co/Tommi)

Feel free to contact us for more details 🤗