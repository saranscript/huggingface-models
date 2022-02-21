---
language: en
tags:
- textual-entailment
- nli
- pytorch
datasets:
- mnli
license: mit
widget :
- text: "EpCAM is overexpressed in breast cancer. </s></s> EpCAM is downregulated in breast cancer."
---

# BiomedNLP-PubMedBERT finetuned on textual entailment (NLI)

The [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext?text=%5BMASK%5D+is+a+tumor+suppressor+gene) finetuned on the MNLI dataset. It should be useful in textual entailment tasks involving biomedical corpora.

## Usage 
Given two sentences (a premise and a hypothesis), the model outputs the logits of entailment, neutral or contradiction. 

You can test the model using the HuggingFace model widget on the side:
- Input two sentences (premise and hypothesis) one after the other.
- The model returns the probabilities of 3 labels: entailment(LABEL:0), neutral(LABEL:1) and contradiction(LABEL:2) respectively.

To use the model locally on your machine: 
```python
# import torch
# device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("lighteternal/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-mnli")
model = AutoModelForSequenceClassification.from_pretrained("lighteternal/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-mnli")

premise = 'EpCAM is overexpressed in breast cancer'
hypothesis = 'EpCAM is downregulated in breast cancer.'

# run through model pre-trained on MNLI
x = tokenizer.encode(premise, hypothesis, return_tensors='pt',
                     truncation_strategy='only_first')
logits = model(x)[0]

probs = logits.softmax(dim=1)
print('Probabilities for entailment, neutral, contradiction \n', np.around(probs.cpu().
                                                                           detach().numpy(),3))
# Probabilities for entailment, neutral, contradiction 
# 0.001 0.001 0.998

```

## Metrics
Evaluation on classification accuracy (entailment, contradiction, neutral) on MNLI test set:

| Metric | Value |
| --- | --- |
| Accuracy | 0.8338|

See Training Metrics tab for detailed info.