---
language: ISO 639-1 code for your language, or `multilingual`
thumbnail: url to a thumbnail used in social sharing
tags:
- array
- of
- tags
datasets:
- array of dataset identifiers
metrics:
- array of metric identifiers
widget:
- text: Copyright infringement is viewed as an infringement of scholarly uprightness
    and a penetrate of editorial morals.
---

# XLNet-LMGC-M for Machine-Paraphrased Plagiarism Detection

This is the checkpoint for LMGC based on XLNet-base after being trained on the Machine-Paraphrased Plagiarism Dataset: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3608000.svg)](https://doi.org/10.5281/zenodo.3608000)

Additional information about this model:

* [The xlnet-base model page](https://huggingface.co/xlnet-base-cased)
* [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf)

The model can be loaded to perform Plagiarism like so:

```py
from transformers import AutoModelForSequenceClassification, AutoTokenizer

AutoModelForSequenceClassification("jpelhaw/xlnet-base-plagiarism-detection")
AutoTokenizer.from_pretrained("jpelhaw/xlnet-base-plagiarism-detection")

input = 'Copyright infringement is viewed as an infringement of scholarly uprightness and a penetrate of editorial morals.'


example = tokenizer.tokenize(input, add_special_tokens=True)

answer = model(**example)
                                
# "plagiarism"
```