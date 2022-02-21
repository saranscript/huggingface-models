---
tags:
- adapter-transformers
- xlm-roberta
- adapterhub:quality_estimation/wmt21
---

# Adapter `Gregor/xlm-roberta-large-wmt21-qe` for xlm-roberta-large

An [adapter](https://adapterhub.ml) for the xlm-roberta-large model that was trained on the [quality_estimation/wmt21](https://adapterhub.ml/explore/quality_estimation/wmt21/) dataset and includes a prediction head for classification.

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

model = AutoModelWithHeads.from_pretrained("xlm-roberta-large")
adapter_name = model.load_adapter("Gregor/xlm-roberta-large-wmt21-qe")
model.active_adapters = adapter_name
```

## Architecture & Training

<!-- Add some description here -->

## Evaluation results

<!-- Add some description here -->

## Citation

<!-- Add some description here -->