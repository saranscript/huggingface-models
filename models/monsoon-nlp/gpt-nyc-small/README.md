# GPT-NYC-small

## About

GPT2 (small version on HF) fine-tuned on questions and responses from https://reddit.com/r/asknyc

I filtered comments to ones with scores >= 3, and responding directly
to the original post ( = ignoring responses to other commenters).
I also added many tokens which were common on /r/AskNYC but missing from
GPT2.

The [gpt-nyc](https://huggingface.co/monsoon-nlp/gpt-nyc) repo is based
on GPT2-Medium and comes off more accurate, but the answers from this
test model struck me as humorous for their strings of subway transfers
or rambling answers about apartments.

Try prompting with ```question?``` plus two spaces, or  ```question? - more info``` plus two spaces

## Blog

https://mapmeld.medium.com/gpt-nyc-part-1-9cb698b2e3d

## Notebooks

### Data processing / new tokens

https://colab.research.google.com/drive/13BOw0uekoAYB4jjQtaXTn6J_VHatiRLu

### Fine-tuning GPT2 (small)

https://colab.research.google.com/drive/1FnXcAh4H-k8dAzixkV5ieygV96ePh3lR

### Predictive text and probabilities

Scroll to end of

https://colab.research.google.com/drive/1FnXcAh4H-k8dAzixkV5ieygV96ePh3lR

to see how to install git-lfs and trick ecco into loading this.
