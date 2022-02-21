# GPT-NYC-affirmations

## About

GPT2 (small version on HF) fine-tuned on questions and responses from https://reddit.com/r/asknyc
and then 2 epochs of [Value Affirmations](https://gist.github.com/mapmeld/c16794ecd93c241a4d6a65bda621bb55)
based on the OpenAI post [Improving Language Model Behavior](https://openai.com/blog/improving-language-model-behavior/)
and corresponding paper.

Try prompting with ```question? - %% ``` or  ```question? - more info %%```

I filtered AskNYC comments to ones with scores >= 3, and responding directly
to the original post ( = ignoring responses to other commenters).
I also added many tokens which were common on /r/AskNYC but missing from
GPT2.

The 'affirmations' list was sourced from excerpts in the OpenAI paper, a popular version of
the 'in this house we believe' sign, and the Reddit rules. They should not
be seen as all-encompassing or foundational to a safe AI. The main goal
was to see how it affected the behavior of GPT-NYC on generating toxic
or non-toxic language.

The [gpt-nyc](https://huggingface.co/monsoon-nlp/gpt-nyc) repo is based
on GPT2-Medium and comes off more accurate.


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
