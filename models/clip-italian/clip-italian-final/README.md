---
language: it
license: 
datasets:
- wit
- ctl/conceptualCaptions
- mscoco-it
tags:
- italian
- bert
- vit
- vision
---

# CLIP-Italian
CLIP Italian is a CLIP-like Model for Italian. The CLIP model (Contrastive Language–Image Pre-training) was developed by researchers at OpenAI and is able to efficiently learn visual concepts from natural language supervision. 

We fine-tuned a competitive Italian CLIP model with only ~1.4 million Italian image-text pairs. This model is part of the [Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organized by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.

## Training Data
We considered three main sources of data: 
- [WIT](https://github.com/google-research-datasets/wit)
- [MSCOCO-IT](https://github.com/crux82/mscoco-it)
- [Conceptual Captions](https://ai.google.com/research/ConceptualCaptions/)

## Training Procedure
Preprocessing, hardware used, hyperparameters...

## Evaluation Performance


## Limitations


## Usage


## Team members
- Federico Bianchi ([vinid](https://huggingface.co/vinid))
- Raphael Pisoni ([4rtemi5](https://huggingface.co/4rtemi5))
- Giuseppe Attanasio ([g8a9](https://huggingface.co/g8a9))
- Silvia Terragni ([silviatti](https://huggingface.co/silviatti))
- Dario Balestri ([D3Reo](https://huggingface.co/D3Reo))
- Gabriele Sarti ([gsarti](https://huggingface.co/gsarti))
- Sri Lakshmi ([srisweet](https://huggingface.co/srisweet))

## Useful links
- [CLIP Blog post](https://openai.com/blog/clip/)
- [CLIP paper](https://arxiv.org/abs/2103.00020)
- [Community Week README](https://github.com/huggingface/transformers/blob/master/examples/research_projects/jax-projects/README.md)
- [Community Week channel](https://discord.com/channels/858019234139602994/859711887520038933)
- [Hybrid CLIP example scripts](https://github.com/huggingface/transformers/tree/master/examples/research_projects/jax-projects/hybrid_clip)
- [Model Repository](https://huggingface.co/clip-italian/clip-italian-final/)