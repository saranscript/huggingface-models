---
language: en
tags:
- go-emotion
- text-classification
- pytorch
datasets:
- go_emotions
metrics:
- f1
widget:
- text: "Thanks for giving advice to the people who need it! 👌🙏"
license: mit
---

## Model Description
1. Based on the uncased BERT pretrained model with a linear output layer.
2. Added several commonly-used emoji and tokens to the special token list of the tokenizer.
3. Did label smoothing while training.
4. Used weighted loss and focal loss to help the cases which trained badly.

## Results
Best Result of `Macro F1` - 70%

## Tutorial Link
- [GitHub](https://github.com/justin871030/GoEmotions)