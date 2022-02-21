---
language: "ca"
tags:
- masked-lm
- BERTa
- catalan
widget:
- text: "El Català és una llengua molt <mask>."
- text: "Salvador Dalí va viure a <mask>."
- text: "La Costa Brava té les millors <mask> d'Espanya."
- text: "El cacaolat és un batut de <mask>."
- text: "<mask> és la capital de la Garrotxa."
- text: "Vaig al <mask> a buscar bolets."
- text: "Antoni Gaudí vas ser un <mask> molt important per la ciutat."
- text: "Catalunya és una referència en <mask> a nivell europeu."
license: apache-2.0
---
# BERTa: RoBERTa-based Catalan language model

<font size="+2">
<strong>
<span style="color:red">
WARNING:
</span>
</strong>
</font>

This repository is now superseded by [BSC-TeMU/roberta-base-ca](https://huggingface.co/BSC-TeMU/roberta-base-ca). Future updates will be released in the new repository, so it is highly recommended to load the model using the new path:

```python
from transformers import AutoModel
model = AutoModel.from_pretrained("BSC-TeMU/roberta-base-ca")
```

From now on, all models and datasets from the BSC's Text Mining Unit will be published on the [official organization account](https://huggingface.co/BSC-TeMU).