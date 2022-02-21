---
language: es
license: cc-by-4.0
tags:
- multilingual
- bert
pipeline_tag: fill-mask
widget:
- text: ¿Qué es la vida? Un [MASK].
---

# ALBERTI

ALBERTI is a set of two BERT-based multilingual model for poetry. One for verses and another one for stanzas. This model has been further trained with the PULPO corpus for verses using [Flax](https://github.com/google/flax), including training scripts.

This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organised by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.

## PULPO

PULPO, the Prodigious Unannotated Literary Poetry Corpus, is a set of multilingual corpora of verses and stanzas with over 95M words.

The following corpora has been downloaded using the [Averell](https://github.com/linhd-postdata/averell/) tool, developed by the [POSTDATA](https://postdata.linhd.uned.es/) team:

### Spanish
- [Disco v3](https://github.com/pruizf/disco)
- [Corpus of Spanish Golden-Age Sonnets](https://github.com/bncolorado/CorpusSonetosSigloDeOro)
- [Corpus general de poesía lírica castellana del Siglo de Oro](https://github.com/bncolorado/CorpusGeneralPoesiaLiricaCastellanaDelSigloDeOro)
- [Gongocorpus](https://github.com/linhd-postdata/gongocorpus) - [source](http://obvil.sorbonne-universite.site/corpus/gongora/gongora_obra-poetica)
### English
- [Eighteenth-Century Poetry Archive (ECPA)](https://github.com/alhuber1502/ECPA)
- [For better for verse](https://github.com/waynegraham/for_better_for_verse)
### French
- [Métrique en Ligne](https://crisco2.unicaen.fr/verlaine/index.php?navigation=accueil) - [source](https://github.com/linhd-postdata/metrique-en-ligne)
### Italian
- [Biblioteca italiana](https://github.com/linhd-postdata/biblioteca_italiana) - [source](http://www.bibliotecaitaliana.it/)
### Czech
- [Corpus of Czech Verse](https://github.com/versotym/corpusCzechVerse)
### Portuguese
- [Stichotheque](https://gitlab.com/stichotheque/stichotheque-pt)

Also, we obtained the following corpora from these sources:
### Spanish 
- [Poesi.as](https://github.com/linhd-postdata/poesi.as) - [source](http://www.poesi.as/)
### English
- [A Gutenberg Poetry Corpus](https://github.com/aparrish/gutenberg-poetry-corpus)
### Arabic
- [Arabic Poetry dataset](https://www.kaggle.com/ahmedabelal/arabic-poetry)
### Chinese
- [THU Chinese Classical Poetry Corpus](https://github.com/THUNLP-AIPoet/Datasets/tree/master/CCPC)
### Finnish
- [SKVR](https://github.com/sks190/SKVR)
### German
- [TextGrid Poetry Corpus](https://github.com/linhd-postdata/textgrid-poetry) - [source](https://textgrid.de/en/digitale-bibliothek)
- [German Rhyme Corpus](https://github.com/tnhaider/german-rhyme-corpus)
### Hungarian
- [verskorpusz](https://github.com/ELTE-DH/verskorpusz)
### Portuguese
- [Poems in Portuguese](https://www.kaggle.com/oliveirasp6/poems-in-portuguese)
### Russian
- [19 000 Russian poems](https://www.kaggle.com/grafstor/19-000-russian-poems)

## Team members

- Álvaro Pérez ([alvp](https://huggingface.co/alvp))
- Javier de la Rosa ([versae](https://huggingface.co/versae))
- Aitor Díaz ([aitordiaz](https://huggingface.co/aitordiaz))
- Elena González-Blanco
- Salvador Ros ([salva](https://huggingface.co/salva))

## Useful links

- [Community Week timeline](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104#summary-timeline-calendar-6)
- [Community Week README](https://github.com/huggingface/transformers/blob/master/examples/research_projects/jax-projects/README.md)
- [Community Week thread](https://discuss.huggingface.co/t/bertin-pretrain-roberta-large-from-scratch-in-spanish/7125)
- [Community Week channel](https://discord.com/channels/858019234139602994/859113060068229190)
- [Masked Language Modelling example scripts](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling)
- [Model Repository](https://huggingface.co/flax-community/alberti-bert-base-multilingual-cased/)

## Acknowledgments

This project would not have been possible without the infrastructure and resources provided by HuggingFace and Google Cloud. Moreover, we want to thank POSTDATA Project (ERC-StG-679528) and the Computational Literary Studies Infrastructure (CLS INFRA No. 101004984) of the European Union's Horizon 2020 research and innovation programme for their support and time allowance.