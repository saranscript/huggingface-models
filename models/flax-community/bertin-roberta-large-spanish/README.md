---
language: es
license: cc-by-4.0
tags:
- spanish
- roberta
pipeline_tag: fill-mask
widget:
- text: Fui a la librería a comprar un <mask>.
---

# NOTE: This repository is now superseded by https://huggingface.co/bertin-project/bertin-roberta-base-spanish. This model corresponds to the `beta` version of the model using stepwise over sampling trained for 200k steps with 128 sequence lengths. Version 1 is now available and should be used instead.

# BERTIN

BERTIN is a series of BERT-based models for Spanish. This one is a RoBERTa-large model trained from scratch on the Spanish portion of mC4 using [Flax](https://github.com/google/flax), including training scripts.

This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organised by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.

## Spanish mC4

The Spanish portion of mC4 containes about 416 million records and 235 billion words.

```bash
$ zcat c4/multilingual/c4-es*.tfrecord*.json.gz | wc -l
416057992
```

```bash
$ zcat c4/multilingual/c4-es*.tfrecord-*.json.gz | jq -r '.text | split(" ") | length' | paste -s -d+ - | bc
235303687795
```

## Team members

- Javier de la Rosa ([versae](https://huggingface.co/versae))
- Eduardo González ([edugp](https://huggingface.co/edugp))
- Paulo Villegas ([paulo](https://huggingface.co/paulo))
- Pablo González de Prado ([Pablogps](https://huggingface.co/Pablogps))
- Manu Romero ([mrm8488](https://huggingface.co/))
- María Grandury ([mariagrandury](https://huggingface.co/))

## Useful links

- [Community Week timeline](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104#summary-timeline-calendar-6)
- [Community Week README](https://github.com/huggingface/transformers/blob/master/examples/research_projects/jax-projects/README.md)
- [Community Week thread](https://discuss.huggingface.co/t/bertin-pretrain-roberta-large-from-scratch-in-spanish/7125)
- [Community Week channel](https://discord.com/channels/858019234139602994/859113060068229190)
- [Masked Language Modelling example scripts](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling)
- [Model Repository](https://huggingface.co/flax-community/bertin-roberta-large-spanish/)
