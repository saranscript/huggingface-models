Graphcore and Hugging Face are working together to make training of Transformer models on IPUs fast and easy. Learn more about how to take advantage of the power of Graphcore IPUs to train Transformers models at [hf.co/hardware/graphcore](https://huggingface.co/hardware/graphcore).

# BERT Base model IPU config

This model contains just the `IPUConfig` files for running the BERT base model (e.g. [bert-base-uncased](https://huggingface.co/bert-base-uncased) or [bert-base-cased](https://huggingface.co/bert-base-cased)) on Graphcore IPUs.

**This model contains no model weights, only an IPUConfig.** 

## Usage

```
from optimum.graphcore import IPUConfig
ipu_config = IPUConfig.from_pretrained("Graphcore/bert-base-ipu")
```