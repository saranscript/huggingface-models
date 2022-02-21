# GPT-NYC

## About

GPT2-Medium fine-tuned on questions and responses from https://reddit.com/r/asknyc

I filtered comments to ones with scores >= 3, and responding directly
to the original post ( = ignoring responses to other commenters).

I added tokens to match NYC neighborhoods, subway stations, foods, and other
common terms in the original batches of questions and comments.
You would be surprised what is missing from GPT tokens!

Try prompting with ```question? %% ``` or  ```question? - more info %%```

## Status

I would like to continue by:
- fine-tuning GPT2-Large with a larger dataset of questions
- examining bias and toxicity
- examining memorization vs. original responses
- releasing a reusable benchmark

## Blog

https://mapmeld.medium.com/gpt-nyc-part-1-9cb698b2e3d

## Notebooks

### Data processing / new tokens

https://colab.research.google.com/drive/13BOw0uekoAYB4jjQtaXTn6J_VHatiRLu

### Fine-tuning GPT2 (small)

https://colab.research.google.com/drive/1FnXcAh4H-k8dAzixkV5ieygV96ePh3lR

### Fine-tuning GPT2-Medium

Same code as small, but on Google Cloud to use an A100 GPU

### Predictive text and probabilities

Scroll to end of

https://colab.research.google.com/drive/1FnXcAh4H-k8dAzixkV5ieygV96ePh3lR

to see how to install git-lfs and trick ecco into loading this.
