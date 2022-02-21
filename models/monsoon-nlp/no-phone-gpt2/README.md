---
language: en
tags:
- exbert

license: mit
---

# no-phone-gpt2

This is a test to remove memorized private information, such as phone numbers, from a small GPT-2 model. This should not generate valid phone numbers.

Inspired by BAIR privacy research:
- https://bair.berkeley.edu/blog/2019/08/13/memorization/
- https://bair.berkeley.edu/blog/2020/12/20/lmmem/

[Blog post](https://mapmeld.medium.com/scrambling-memorized-info-in-gpt-2-60753d7652d8)

## Process

- All +## and +### tokens were replaced with new, randomly-selected 2- and 3-digit numbers in the vocab.json and tokenizer.json. You can identify these in outputs because the new tokens start with ^^.
- Input and output embeddings for +## and +### tokens were moved to the +00 and +000 embeddings.
- Removed associations between numbers from merges.txt

Using a library such as [ecco](https://github.com/jalammar/ecco), probabilities for next number token look equally likely, with +000 preferred.

Code: https://colab.research.google.com/drive/1X31TIZjmxlXMXAzQrR3Fl1AnLzGBCpWf#scrollTo=0GVFwrAgY68J

### Future goals

- Add new +### tokens to rebuild number generation
- Fine-tune new tokens on counting numbers and ended phone numbers
- Use [gpt2-large](https://huggingface.co/gpt2-large)

### BibTeX entry and citation info

Original GPT-2:

```bibtex
@article{radford2019language,
  title={Language Models are Unsupervised Multitask Learners},
  author={Radford, Alec and Wu, Jeff and Child, Rewon and Luan, David and Amodei, Dario and Sutskever, Ilya},
  year={2019}
}
```
