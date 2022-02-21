---
language: "fr"

tags:
- french
- gpt2
- model
---

A small french language model for french text generation (and possibly more NLP tasks...)

**Introduction**

This french gpt2 model is based on openai GPT-2 small model.

It was trained on a <b>very small (190Mb) dataset </b> from french wikipedia using Transfer Learning and Fine-tuning techniques in just over a day, on one Colab pro with 1GPU 16GB.

It was created applying the recept of <b>Pierre Guillou</b>

See https://medium.com/@pierre_guillou/faster-than-training-from-scratch-fine-tuning-the-english-gpt-2-in-any-language-with-hugging-f2ec05c98787

It is a proof-of-concept that makes possible to get a language model in any language with low ressources.

It was fine-tuned from the English pre-trained GPT-2 small using the Hugging Face libraries (Transformers and Tokenizers) wrapped into the fastai v2 Deep Learning framework. All the fine-tuning fastai v2 techniques were used.

It is now available on Hugging Face. For further information or requests, please go to "Faster than training from scratch — Fine-tuning the English GPT-2 in any language with Hugging Face and fastai v2 (practical case with Portuguese)".

Model migth be improved by using larger dataset under larger powerful training infrastructure. At least this one can be used for small finetuning experimentation (i.e with aitextgen).

PS : I've lost the metrics but it speaks french with some minor grammar issues, coherence of text is somehow limited.   