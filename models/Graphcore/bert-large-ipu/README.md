Graphcore and Hugging Face are working together to make training of Transformer models on IPUs fast and easy. Learn more about how to take advantage of the power of Graphcore IPUs to train Transformers models at [hf.co/hardware/graphcore](https://huggingface.co/hardware/graphcore).

# BERT Large model IPU config

This model contains just the `IPUConfig` files for running the BERT large model (e.g. [bert-large-uncased](https://huggingface.co/bert-large-uncased) or [bert-large-cased](https://huggingface.co/bert-large-cased)) on Graphcore IPUs.

**This model contains no model weights, only an IPUConfig.** 

## Usage

```
from optimum.graphcore import IPUConfig
ipu_config = IPUConfig.from_pretrained("Graphcore/bert-large-ipu")
```