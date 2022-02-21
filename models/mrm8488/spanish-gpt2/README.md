---
language: es
tags:
- GPT-2
datasets:
 - large_spanish_corpus
widgets:
- text: "Érase un vez un"

license: mit

---
# Spanish GPT-2 trained on [large_spanish_corpus](https://huggingface.co/datasets/viewer/?dataset=large_spanish_corpus)

This is a Spanish GPT-2 model trained from scratch on the [large_spanish_corpus](https://huggingface.co/datasets/viewer/?dataset=large_spanish_corpus) aka BETO's corpus with [Flax](https://github.com/google/flax)
This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organised by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.
## Dataset
The dataset is about 20 GB. 95% of the data was used for training and the rest 5% for validation.

## Metrics (on evaluation dataset)

- Loss: 2.413
- Perplexity: 11.36

## Team members
- Manuel Romero ([mrm8488](https://huggingface.co/mrm8488))
- María Grandury ([mariagrandury](https://huggingface.co/))
- Pablo González de Prado ([Pablogps](https://huggingface.co/Pablogps))
- Daniel Vera ([daveni](https://huggingface.co/daveni))
- Sri Lakshmi ([srisweet](https://huggingface.co/srisweet))
- José Posada ([jdposa](https://huggingface.co/jdposa))
- Santiago Hincapie ([shpotes](https://huggingface.co/shpotes))
- Jorge ([jorgealro](https://huggingface.co/jorgealro))


## Useful links
- [Community Week timeline](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104#summary-timeline-calendar-6)
- [Community Week README](https://github.com/huggingface/transformers/blob/master/examples/research_projects/jax-projects/README.md)
- [Community Week thread](https://discuss.huggingface.co/t/pretrain-gpt2-from-scratch-in-spanish/7086/8)