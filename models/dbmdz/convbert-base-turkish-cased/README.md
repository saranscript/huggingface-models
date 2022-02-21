---
language: tr
license: mit
---

# 🤗 + 📚 dbmdz Turkish ConvBERT model

In this repository the MDZ Digital Library team (dbmdz) at the Bavarian State
Library open sources a cased ConvBERT model for Turkish 🎉

# 🇹🇷 ConvBERTurk

ConvBERTurk is a community-driven cased ConvBERT model for Turkish.

In addition to the BERT and ELECTRA based models, we also trained a ConvBERT model. The ConvBERT architecture is presented
in the ["ConvBERT: Improving BERT with Span-based Dynamic Convolution"](https://arxiv.org/abs/2008.02496) paper.

We follow a different training procedure: instead of using a two-phase approach, that pre-trains the model for 90% with 128
sequence length and 10% with 512 sequence length, we pre-train the model with 512 sequence length for 1M steps on a v3-32 TPU.

## Stats

The current version of the model is trained on a filtered and sentence
segmented version of the Turkish [OSCAR corpus](https://traces1.inria.fr/oscar/),
a recent Wikipedia dump, various [OPUS corpora](http://opus.nlpl.eu/) and a
special corpus provided by [Kemal Oflazer](http://www.andrew.cmu.edu/user/ko/).

The final training corpus has a size of 35GB and 44,04,976,662 tokens.

Thanks to Google's TensorFlow Research Cloud (TFRC) we could train a cased model
on a TPU v3-32!

## Usage

With Transformers >= 4.3 our cased ConvBERT model can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

model_name = "dbmdz/convbert-base-turkish-cased"

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
```

## Results

For results on PoS tagging, NER and Question Answering downstream tasks, please refer to
[this repository](https://github.com/stefan-it/turkish-bert).

# Huggingface model hub

All models are available on the [Huggingface model hub](https://huggingface.co/dbmdz).

# Contact (Bugs, Feedback, Contribution and more)

For questions about our DBMDZ BERT models in general, just open an issue
[here](https://github.com/dbmdz/berts/issues/new) 🤗

# Acknowledgments

Thanks to [Kemal Oflazer](http://www.andrew.cmu.edu/user/ko/) for providing us
additional large corpora for Turkish. Many thanks to Reyyan Yeniterzi for providing
us the Turkish NER dataset for evaluation.

Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC).
Thanks for providing access to the TFRC ❤️

Thanks to the generous support from the [Hugging Face](https://huggingface.co/) team,
it is possible to download both cased and uncased models from their S3 storage 🤗
