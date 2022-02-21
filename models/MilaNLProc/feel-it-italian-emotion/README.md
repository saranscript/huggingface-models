---

language: it

license: mit

tags:

- sentiment

- emotion

- Italian

---

# FEEL-IT: Emotion and Sentiment Classification for the Italian Language

## FEEL-IT Python Package

You can find the package that uses this model for emotion and sentiment classification **[here](https://github.com/MilaNLProc/feel-it)** it is meant to be a very simple interface over HuggingFace models.

## Abstract

Sentiment analysis is a common task to understand people's reactions online. Still, we often need more nuanced information: is the post negative because the user is angry or because they are sad?

An abundance of approaches has been introduced for tackling both tasks. However, at least for Italian, they all treat only one of the tasks at a time. We introduce *FEEL-IT*, a novel benchmark corpus of Italian Twitter posts annotated with four basic emotions: **anger, fear, joy, sadness**. By collapsing them, we can also do **sentiment analysis**. We evaluate our corpus on benchmark datasets for both emotion and sentiment classification, obtaining competitive results.

We release an [open-source Python library](https://github.com/MilaNLProc/feel-it), so researchers can use a model trained on FEEL-IT for inferring both sentiments and emotions from Italian text.

| Model                       | Download |
| ------                      | -------------------------|
| `feel-it-italian-sentiment` | [Link](https://huggingface.co/MilaNLProc/feel-it-italian-sentiment) |
| `feel-it-italian-emotion`   | [Link](https://huggingface.co/MilaNLProc/feel-it-italian-emotion) | 

## Model

The *feel-it-italian-emotion* model performs **emotion classification (joy, fear, anger, sadness)** on Italian. We fine-tuned the [UmBERTo model](https://huggingface.co/Musixmatch/umberto-commoncrawl-cased-v1) on our new dataset (i.e., FEEL-IT) obtaining state-of-the-art performances on different benchmark corpora.

## Data

Our data has been collected by annotating tweets from a broad range of topics. In total, we have 2037 tweets annotated with an emotion label. More details can be found in our paper (preprint available soon).

## Performance

We evaluate our performance using [MultiEmotions-It](http://ceur-ws.org/Vol-2769/paper_08.pdf). This dataset differs from FEEL-IT both in terms of topic variety and considered social media (i.e., YouTube and Facebook). We considered only the subset of emotions present in FEEL-IT. To give a point of reference, we also show the Most Frequent Class (MFC) baseline results. The results show that training on FEEL-IT brings stable performance even on datasets from different contexts.

| Training Dataset | Macro-F1 | Accuracy
| ------ | ------ |------ |
| MFC | 0.20 | 0.64  |
| FEEL-IT | **0.57** | **0.73**  |

## Usage

```python

import torch
import numpy as np 
from transformers import AutoTokenizer, AutoModelForSequenceClassification

# Load model and tokenizer
tokenizer = AutoTokenizer.from_pretrained("MilaNLProc/feel-it-italian-emotion")
model = AutoModelForSequenceClassification.from_pretrained("MilaNLProc/feel-it-italian-emotion")

sentence = 'Oggi sono proprio contento!'
inputs = tokenizer(sentence, return_tensors="pt")

# Call the model and get the logits
labels = torch.tensor([1]).unsqueeze(0)  # Batch size 1
outputs = model(**inputs, labels=labels)
loss, logits = outputs[:2]
logits = logits.squeeze(0)

# Extract probabilities
proba = torch.nn.functional.softmax(logits, dim=0)
proba = np.array(proba.detach().numpy())

# Obtain emotion probabilities (sorted)
label_names = ['anger', 'fear', 'joy', 'sadness']
ranking = np.argsort(proba)
ranking = ranking[::-1]
for i in range(proba.shape[0]):
    l = label_names[ranking[i]]
    s = proba[ranking[i]]
    print(f"{l} {np.round(float(s), 4)}")

```

## Citation

Please use the following bibtex entry if you use this model in your project:

```
@inproceedings{bianchi2021feel,
    title = {{"FEEL-IT: Emotion and Sentiment Classification for the Italian Language"}},
    author = "Bianchi, Federico and Nozza, Debora and Hovy, Dirk",
    booktitle = "Proceedings of the 11th Workshop on Computational Approaches to Subjectivity, Sentiment and Social Media Analysis",
    year = "2021",
    publisher = "Association for Computational Linguistics",
}
```