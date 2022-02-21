Graphcore and Hugging Face are working together to make training of Transformer models on IPUs fast and easy. Learn more about how to take advantage of the power of Graphcore IPUs to train Transformers models at [hf.co/hardware/graphcore](https://huggingface.co/hardware/graphcore).

# ViT Base model IPU config

This model contains just the `IPUConfig` files for running the ViT base model (e.g. [vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) or [deit-base-patch16-384](https://huggingface.co/facebook/deit-base-patch16-384)) on Graphcore IPUs.

**This model contains no model weights, only an IPUConfig.** 

## Usage

```
from optimum.graphcore import IPUConfig
ipu_config = IPUConfig.from_pretrained("Graphcore/vit-base-ipu")
```