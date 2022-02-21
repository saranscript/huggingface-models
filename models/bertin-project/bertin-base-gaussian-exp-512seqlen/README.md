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

This is a **RoBERTa-base** model trained from scratch in Spanish.

The training dataset is [mc4](https://huggingface.co/datasets/bertin-project/mc4-es-sampled ) subsampling documents to a total of about 50 million examples. Sampling is biased towards average perplexity values (using a Gaussian function), discarding more often documents with very large values (poor quality) of very small values (short, repetitive texts).

This model takes the one using [sequence length 128](https://huggingface.co/bertin-project/bertin-base-gaussian) and trains during 25.000 steps using sequence length 512.

Please see our main [card](https://huggingface.co/bertin-project/bertin-roberta-base-spanish) for more information.

This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organised by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.


## Team members

- Eduardo González ([edugp](https://huggingface.co/edugp))
- Javier de la Rosa ([versae](https://huggingface.co/versae))
- Manu Romero ([mrm8488](https://huggingface.co/))
- María Grandury ([mariagrandury](https://huggingface.co/))
- Pablo González de Prado ([Pablogps](https://huggingface.co/Pablogps))
- Paulo Villegas ([paulo](https://huggingface.co/paulo))