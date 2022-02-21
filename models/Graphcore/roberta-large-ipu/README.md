Graphcore and Hugging Face are working together to make training of Transformer models on IPUs fast and easy. Learn more about how to take advantage of the power of Graphcore IPUs to train Transformers models at [hf.co/hardware/graphcore](https://huggingface.co/hardware/graphcore).

# RoBERTa Large model IPU config

This model contains just the `IPUConfig` files for running the [roberta-large](https://huggingface.co/roberta-large) model on Graphcore IPUs.

**This model contains no model weights, only an IPUConfig.** 

## Usage

```

from optimum.graphcore import IPUConfig

ipu_config = IPUConfig.from_pretrained("Graphcore/roberta-large-ipu")

```