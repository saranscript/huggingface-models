---
language: ar
license: apache-2.0
---

# Arabic-Flip-mT5

An [mT5-small](https://huggingface.co/google/mt5-small) model fine-tuned on the
Arabic Parallel Gender Corpus v2.0.  You should be able to do gender inflection
(M->F or F->M) in Arabic.

Uses: Data augmentation, detecting gender bias of a model, obfuscating gender of a user/customer.

## Training Notebook

https://colab.research.google.com/drive/1w3XY9yClfDo1T-1mc19W39i2aceK2d1D?usp=sharing

## Caveats
- The Parallel Gender Corpus is trained on subtitles with mostly first- and second-person sentences, so it is less likely to handle third-person references or longer texts.
- Used mT5-small and batch size of 4, due to CoLab GPU constraints; should ++
- Ran 1 epoch due to an issue with CoLab
