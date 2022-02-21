---
language: de
license: mit
tags:
  - "historic german"
---

# 🤗 + 📚 dbmdz DistilBERT model

In this repository the MDZ Digital Library team (dbmdz) at the Bavarian State
Library open sources a German Europeana DistilBERT model 🎉

# German Europeana DistilBERT

We use the open source [Europeana newspapers](http://www.europeana-newspapers.eu/)
that were provided by *The European Library*. The final
training corpus has a size of 51GB and consists of 8,035,986,369 tokens.

Detailed information about the data and pretraining steps can be found in
[this repository](https://github.com/stefan-it/europeana-bert).

## Results

For results on Historic NER, please refer to [this repository](https://github.com/stefan-it/europeana-bert).

## Usage

With Transformers >= 4.3 our German Europeana DistilBERT model can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

model_name = "distilbert-base-german-europeana-cased"

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
```

# Huggingface model hub

All other German Europeana models are available on the [Huggingface model hub](https://huggingface.co/dbmdz).

# Contact (Bugs, Feedback, Contribution and more)

For questions about our Europeana BERT, ELECTRA and ConvBERT models just open a new discussion
[here](https://github.com/stefan-it/europeana-bert/discussions) 🤗

# Acknowledgments

Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC).
Thanks for providing access to the TFRC ❤️

Thanks to the generous support from the [Hugging Face](https://huggingface.co/) team,
it is possible to download both cased and uncased models from their S3 storage 🤗