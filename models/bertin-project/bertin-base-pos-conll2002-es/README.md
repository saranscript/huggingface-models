---
language: es
license: cc-by-4.0
tags:
- spanish
- roberta
- ner
---

This checkpoint has been trained for the POS task using the CoNLL 2002-es dataset.

This checkpoint was created from **Bertin Gaussian 512**, which is a **RoBERTa-base** model trained from scratch in Spanish. Information on this base model may be found at [its own card](https://huggingface.co/bertin-project/bertin-base-gaussian-exp-512seqlen) and at deeper detail on [the main project card](https://huggingface.co/bertin-project/bertin-roberta-base-spanish). 

The training dataset for the base model is [mc4](https://huggingface.co/datasets/bertin-project/mc4-es-sampled ) subsampling documents to a total of about 50 million examples. Sampling is biased towards average perplexity values (using a Gaussian function), discarding more often documents with very large values (poor quality) of very small values (short, repetitive texts).

This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organised by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.


## Team members

- Eduardo González ([edugp](https://huggingface.co/edugp))
- Javier de la Rosa ([versae](https://huggingface.co/versae))
- Manu Romero ([mrm8488](https://huggingface.co/))
- María Grandury ([mariagrandury](https://huggingface.co/))
- Pablo González de Prado ([Pablogps](https://huggingface.co/Pablogps))
- Paulo Villegas ([paulo](https://huggingface.co/paulo))