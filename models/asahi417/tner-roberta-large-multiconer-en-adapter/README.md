---
tags:
- adapter-transformers
- adapterhub:named-entity-recognition/multiconer
- roberta
datasets:
- multiconer
---

# Adapter `asahi417/tner-roberta-large-multiconer-en-adapter` for roberta-large

An [adapter](https://adapterhub.ml) for the `roberta-large` model that was trained on the [named-entity-recognition/multiconer](https://adapterhub.ml/explore/named-entity-recognition/multiconer/) dataset and includes a prediction head for tagging.

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

model = AutoModelWithHeads.from_pretrained("roberta-large")
adapter_name = model.load_adapter("asahi417/tner-roberta-large-multiconer-en-adapter", source="hf", set_active=True)
```

## Architecture & Training

<!-- Add some description here -->

## Evaluation results

<!-- Add some description here -->

## Citation

<!-- Add some description here -->