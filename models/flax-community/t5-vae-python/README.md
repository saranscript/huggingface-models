---
language: python
tags: vae
license: apache-2.0
datasets: Fraser/python-lines
---

# T5-VAE-Python (flax)

A Transformer-VAE made using flax.

Try the [demo](https://huggingface.co/spaces/flax-community/t5-vae)!

It has been trained to interpolate on lines of Python code from the [python-lines dataset](https://huggingface.co/datasets/Fraser/python-lines).

Done as part of Huggingface community training ([see forum post](https://discuss.huggingface.co/t/train-a-vae-to-interpolate-on-english-sentences/7548)).

Builds on T5, using an autoencoder to convert it into an MMD-VAE ([more info](http://fras.uk/ml/large%20prior-free%20models/transformer-vae/2020/08/13/Transformers-as-Variational-Autoencoders.html)).

## How to use from the 🤗/transformers library

Add model repo as a submodule:
```bash
git submodule add https://github.com/Fraser-Greenlee/t5-vae-flax.git t5_vae_flax
```

```python
from transformers import AutoTokenizer
from t5_vae_flax.src.t5_vae import FlaxT5VaeForAutoencoding

tokenizer = AutoTokenizer.from_pretrained("t5-base")

model = FlaxT5VaeForAutoencoding.from_pretrained("flax-community/t5-vae-python")
```

## Setup

Run `setup_tpu_vm_venv.sh` to setup a virtual enviroment on a TPU VM for training.
