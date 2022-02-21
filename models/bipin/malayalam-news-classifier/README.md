---
license: mit
tags:
 - text-classification
 - roberta
 - malayalam
 - pytorch
widget:
  - text: "2032 ഒളിമ്പിക്‌സിന് ബ്രിസ്‌ബെയ്ന്‍ വേദിയാകും; ഗെയിംസിന് വേദിയാകുന്ന മൂന്നാമത്തെ ഓസ്‌ട്രേലിയന്‍ നഗരം"
---
## Malayalam news classifier

### Overview

This model is trained on top of [MalayalamBert](https://huggingface.co/eliasedwin7/MalayalamBERT) for the task of classifying malayalam news headlines. Presently, the following news categories are supported:

* Business
* Sports
* Entertainment

### Dataset

The dataset used for training this model can be found [here](https://www.kaggle.com/disisbig/malyalam-news-dataset).

### Using the model with HF pipeline

```python
from transformers import pipeline

news_headline = "ക്രിപ്‌റ്റോ ഇടപാടുകളുടെ വിവരങ്ങൾ ആവശ്യപ്പെട്ട് ആദായനികുതി വകുപ്പ് നോട്ടീസയച്ചു"
model = pipeline(task="text-classification", model="bipin/malayalam-news-classifier")

model(news_headline)
# Output
# [{'label': 'business', 'score': 0.9979357123374939}]
```

### Contact

For feedback and questions, feel free to contact via twitter [@bkrish_](https://twitter.com/bkrish_)