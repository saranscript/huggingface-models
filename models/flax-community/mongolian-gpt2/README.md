---
language: "mn"
thumbnail: "https://avatars.githubusercontent.com/u/43239645?s=60&v=4"
tags:
- gpt2
datasets:
- oscar
---

# Mongolian GPT2

Goal is to create a strong language generation model for Mongolian
Since initial code and data is pretty much written by @patrickvonplaten and other huggingface members, it should not be so hard to get the first sense.

## Model
Randomly initialized GPT2 model

## Datasets
We can use OSCAR which is available through datasets

## Datasets
A causal language modeling script for Flax is available here 1. It can be used pretty much without any required code changes.
If there is time left, I’d love to try some private crawling and integrate it datasets.

## Expected Outcome
Understandable Mongolian text generation model

## Challenges
Lack of data → OSCAR Mongolian is just 2.2G. Maybe we need to research ways to acquire more data with this.