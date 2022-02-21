---
tags:
- bert
- adapterhub:text-classification
- adapter-transformers
---

# Adapter `davanstrien/book-genre-classification` for bert-base-cased

An [adapter](https://adapterhub.ml) for the `bert-base-cased` model that was trained on the [text-classification](https://adapterhub.ml/explore/text-classification/) dataset and includes a prediction head for classification.

This adapter was created for usage with the **[adapter-transformers](https://github.com/Adapter-Hub/adapter-transformers)** library.

## Usage

First, install `adapter-transformers`:

```
pip install -U adapter-transformers
```
_Note: adapter-transformers is a fork of transformers that acts as a drop-in replacement with adapter support. [More](https://docs.adapterhub.ml/installation.html)_

Now, the adapter can be loaded and activated like this:

```python
from transformers import AutoModelWithHeads

model = AutoModelWithHeads.from_pretrained("bert-base-cased")
adapter_name = model.load_adapter("davanstrien/book-genre-classification", source="hf", set_active=True)
```

## Architecture & Training

<!-- Add some description here -->

## Evaluation results

<!-- Add some description here -->

## Citation

<!-- Add some description here -->