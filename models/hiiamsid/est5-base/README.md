---
language: ["es"]
tags:
- spanish
license: mit
---
This is a smaller version of the [google/mt5-base](https://huggingface.co/google/mt5-base) model with only Spanish embeddings left. 
* The original model has 582M parameters, with 237M of them being input and output embeddings. 
* After shrinking the `sentencepiece` vocabulary from 250K to 25K (top 25K Spanish tokens) the number of model parameters reduced to 237M parameters, and model size reduced from 2.2GB to 0.9GB - 42% of the original one.

## Citing & Authors
- Datasets : [cleaned corpora](https://github.com/crscardellino/sbwce)
- Model : [google/mt5-base](https://huggingface.co/google/mt5-base)
- Reference: [cointegrated/rut5-base](https://huggingface.co/cointegrated/rut5-base)
