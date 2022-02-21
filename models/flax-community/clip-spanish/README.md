---
language: es
license: cc-by-4.0
tags:
- spanish
- roberta
- vit
---
# CLIP-Spanish

CLIP Spanish is a CLIP-like model for Spanish language. It is composed of [BERTIN](https://huggingface.co/bertin-project/bertin-roberta-base-spanish) as a language encoder and the ViT-B/32 image encoder from [CLIP](https://huggingface.co/openai/clip-vit-base-patch32). The model is implemented in [Flax](https://github.com/google/flax), including training scripts (see `training.md`).
This is part of the [Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organised by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.

## Spanish WIT

We used a subset of 141,230 Spanish captions from the [WIT dataset](https://github.com/google-research-datasets/wit) for training.

## Team members

- Eduardo González Ponferrada ([edugp](https://huggingface.co/edugp))
- Manu Romero ([mrm8488](https://huggingface.co/))
- María Grandury ([mariagrandury](https://huggingface.co/))

## Useful links

- [Community Week timeline](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104#summary-timeline-calendar-6)
- [Community Week README](https://github.com/huggingface/transformers/blob/master/examples/research_projects/jax-projects/README.md)
- [Community Week thread](https://discuss.huggingface.co/t/bertin-pretrain-roberta-large-from-scratch-in-spanish/7125)
- [Community Week channel](https://discord.com/channels/858019234139602994/859113060068229190)
- [Hybrid CLIP example scripts](https://github.com/huggingface/transformers/tree/master/examples/research_projects/jax-projects/hybrid_clip)
- [Model Repository](https://huggingface.co/flax-community/bertin-roberta-large-spanish/)
