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
- text: Plagiarism is the representation of another author's writing, thoughts, ideas,
    or expressions as one's own work.
---

# Longformer-base for Word Sense Disambiguation

This is the checkpoint for Longformer-base after being trained on the [Machine-Paraphrased Plagiarism Dataset](https://doi.org/10.5281/zenodo.3608000)

Additional information about this model:

* [The longformer-base-4096 model page](https://huggingface.co/allenai/longformer-base-4096)
* [Longformer: The Long-Document Transformer](https://arxiv.org/pdf/2004.05150.pdf)
* [Official implementation by AllenAI](https://github.com/allenai/longformer)

The model can be loaded to perform Plagiarism like so:

```py
from transformers import AutoModelForSequenceClassification, AutoTokenizer

AutoModelForSequenceClassification("jpelhaw/longformer-base-plagiarism-detection")
AutoTokenizer.from_pretrained("jpelhaw/longformer-base-plagiarism-detection")

input = 'Plagiarism is the representation of another author's writing, thoughts, ideas, or expressions as one's own work.'


example = tokenizer.tokenize(input, add_special_tokens=True)

answer = model(**example)
                                
# "plagiarised"
```