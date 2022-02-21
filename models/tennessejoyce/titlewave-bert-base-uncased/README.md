---
language: en
license: cc-by-4.0
widget:
- text: "[Gmail API] How can I extract plain text from an email sent to me?"
---

# Titlewave: bert-base-uncased

## Model description

Titlewave is a Chrome extension that helps you choose better titles for your Stack Overflow questions. See the [github repository](https://github.com/tennessejoyce/TitleWave) for more information.
This is one of two NLP models used in the Titlewave project, and its purpose is to classify whether question will be answered or not just based on the title. The [companion model](https://huggingface.co/tennessejoyce/titlewave-t5-small) suggests a new title based on on the body of the question.

## Intended use

Try out different titles for your Stack Overflow post, and see which one gives you the best chance of receiving an answer.
You can use the model through the API on this page (hosted by HuggingFace) or install the Chrome extension by following the instructions on the [github repository](https://github.com/tennessejoyce/TitleWave), which integrates the tool directly into the Stack Overflow website.

You can also run the model locally in Python like this (which automatically downloads the model to your machine):

```python
>>> from transformers import pipeline
>>> classifier = pipeline('sentiment-analysis', model='tennessejoyce/titlewave-bert-base-uncased')
>>> classifier('[Gmail API] How can I extract plain text from an email sent to me?')

[{'label': 'Answered', 'score': 0.8053370714187622}]
```
The 'score' in the output represents the probability of getting an answer with this title: 80.5%.


## Training data

The weights were initialized from the [BERT base model](https://huggingface.co/bert-base-uncased), which was trained on BookCorpus and English Wikipedia.
Then the model was fine-tuned on the dataset of previous Stack Overflow post titles, which is publicly available [here](https://archive.org/details/stackexchange).
Specifically I used three years of posts from 2017-2019, filtered out posts which were closed (e.g., duplicates, off-topic), and selected 5% of the remaining posts at random to use in the training set, and the same amount for validation and test sets (278,155 posts each).

## Training procedure

The model was fine-tuned for two epochs with a batch size of 32 (17,384 steps total) using 16-bit mixed precision.
After some hyperparameter tuning, I found that the following two-phase training procedure yields the best performance (ROC-AUC score) on the validation set:
* In the first epoch, all layers were frozen except for the last two (pooling layer and classification layer) and a learning rate of 3e-4 was used.
* In the second epoch all layers were unfrozen, and the learning rate was decreased by a factor of 10 to 3e-5.

Otherwise, all parameters we set to the defaults listed [here](https://huggingface.co/transformers/main_classes/trainer.html#transformers.TrainingArguments),
including the AdamW optimizer and a linearly decreasing learning schedule (both of which were reset between the two epochs). See the [github repository](https://github.com/tennessejoyce/TitleWave) for the scripts that were used to train the model.

## Evaluation

See [this notebook](https://github.com/tennessejoyce/TitleWave/blob/master/model_training/test_classifier.ipynb) for the performance of the title classification model on the test set.

