---
tags:
- adapter-transformers
- adapterhub:other
- xlm-roberta
datasets:
- ghadeermobasher/BC5CDR-Chemical-Disease
---

# Adapter `ghadeermobasher/BC5CDR-Chemical-Disease-balanced-SapBERT-UMLS-2020AB-all-lang-from-XLMR` for ghadeermobasher/BC5CDR-Chemical-Disease-balanced-SapBERT-UMLS-2020AB-all-lang-from-XLMR

An [adapter](https://adapterhub.ml) for the `ghadeermobasher/BC5CDR-Chemical-Disease-balanced-SapBERT-UMLS-2020AB-all-lang-from-XLMR` model that was trained on the [other](https://adapterhub.ml/explore/other/) dataset.

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

model = AutoModelWithHeads.from_pretrained("ghadeermobasher/BC5CDR-Chemical-Disease-balanced-SapBERT-UMLS-2020AB-all-lang-from-XLMR")
adapter_name = model.load_adapter("ghadeermobasher/BC5CDR-Chemical-Disease-balanced-SapBERT-UMLS-2020AB-all-lang-from-XLMR", source="hf", set_active=True)
```

## Architecture & Training

<!-- Add some description here -->

## Evaluation results

<!-- Add some description here -->

## Citation

<!-- Add some description here -->