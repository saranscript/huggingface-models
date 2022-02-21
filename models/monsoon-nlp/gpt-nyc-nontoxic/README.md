# GPT-NYC-nontoxic

## About

GPT2 (small version on HF) fine-tuned on questions and responses from https://reddit.com/r/asknyc

I filtered comments to ones with scores >= 3, and responding directly
to the original post ( = ignoring responses to other commenters).
I also added many tokens which were common on /r/AskNYC but missing from
GPT2.

Additional <Toxic> and <NonToxic> tokens control following output.
Toxic comments (about 5.5% of input data) are those which were flagged
by [Perspective API](https://developers.perspectiveapi.com) with toxicity > 0.7,
or by [English DeHateBERT](https://huggingface.co/Hate-speech-CNERG/dehatebert-mono-english),
with <NonToxic> tagging for all comments related to LGBTQ identity 
to avoid false positives / more aggressive censorship from these classifiers.

Try prompting with ```question? - additional info %% <Toxic> ```
Or ```question? - additional info %% <NonToxic>```

## Other options

The [gpt-nyc-small](https://huggingface.co/monsoon-nlp/gpt-nyc-small) repo is based
on GPT2 [small] but without the <Toxic> and <NonToxic> tags. It is the most
directly comparable model to this one.

The main [gpt-nyc](https://huggingface.co/monsoon-nlp/gpt-nyc) repo is based
on GPT2-Medium and comes off more accurate. It does not have Toxic/NonToxic tagging.

## Blog

Initial model: https://mapmeld.medium.com/gpt-nyc-part-1-9cb698b2e3d

## Notebooks

### Data processing / new tokens

https://colab.research.google.com/drive/13BOw0uekoAYB4jjQtaXTn6J_VHatiRLu

### Fine-tuning GPT2 (small)

https://colab.research.google.com/drive/1FnXcAh4H-k8dAzixkV5ieygV96ePh3lR

### Predictive text and probabilities

Scroll to end of

https://colab.research.google.com/drive/1FnXcAh4H-k8dAzixkV5ieygV96ePh3lR

to see how to install git-lfs and trick ecco into loading this.
