---
language:
- en
license: lgpl-3.0
tags:
- text-classification
- transformers
- tf
metrics:
- accuracy
- f1
- precision
- recall
widget:
- text: This pandemic has shown us clearly the vulgarity of our healthcare "system." Highest costs in the world, yet not enough nurses or doctors. Many millions uninsured, while insurance company profits soar. The struggle continues. Healthcare is a human right. Medicare for all.
  example_title: "Bernie Sanders"
---

# distilbert-political-tweets

*Note: model needs to be trained on more current data*

🗣 🇺🇸 Classify sentiment as Democratic or Republican.

# Model

[DistilBERT base model (uncased)](https://huggingface.co/distilbert-base-uncased) for sequence classification fine-tuned on ~10,000 randomly selected tweets from Democratic and Republican senators from FiveThirtyEight's [twitter-ratio/senators](https://fivethirtyeight.datasettes.com/fivethirtyeight/twitter-ratio%2Fsenators#export) dataset.

# Evaluation

The model was evaluated on a validation dataset of ~3,000 unseen random tweets:
```python
{'eval_accuracy': 0.9348,
 'eval_f1': 0.9386,
 'eval_loss': 0.1975,
 'eval_precision': 0.9281,
 'eval_recall': 0.9494}
```