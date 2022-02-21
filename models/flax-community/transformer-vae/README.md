# Transformer-VAE (flax) (WIP)

A Transformer-VAE made using flax.

Done as part of Huggingface community training ([see forum post](https://discuss.huggingface.co/t/train-a-vae-to-interpolate-on-english-sentences/7548)).

Builds on T5, using an autoencoder to convert it into an MMD-VAE.

[See training logs.](https://wandb.ai/fraser/flax-vae)

## ToDo

- [ ] Basic training script working. (Fraser + Theo)
- [ ] Add MMD loss (Theo)

- [ ] Save a wikipedia sentences dataset to Huggingface (see original https://github.com/ChunyuanLI/Optimus/blob/master/data/download_datasets.md) (Mina)
- [ ] Make a tokenizer using the OPTIMUS tokenized dataset.
- [ ] Train on the OPTIMUS wikipedia sentences dataset.

- [ ] Make Huggingface widget interpolating sentences! (???) https://github.com/huggingface/transformers/tree/master/examples/research_projects/jax-projects#how-to-build-a-demo

Optional ToDos:

- [ ] Add Funnel transformer encoder to FLAX (don't need weights).
- [ ] Train a Funnel-encoder + T5-decoder transformer VAE.

- [ ] Additional datasets:
- [ ] Poetry (https://www.gwern.net/GPT-2#data-the-project-gutenberg-poetry-corpus)
- [ ] 8-bit music (https://github.com/chrisdonahue/LakhNES)

## Setup

Follow all steps to install dependencies from https://cloud.google.com/tpu/docs/jax-quickstart-tpu-vm

- [ ] Find dataset storage site.
- [ ] Ask JAX team for dataset storage.
