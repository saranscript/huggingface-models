ParsBERT digikala sentiment analysis model fine-tuned on around 600,000 Persian tweets.
# How to use
at least you need 650 megabytes of ram and disk in order to load the model.
tensorflow, transformers and numpy library

## Loading model
```python
import numpy as np
from transformers import AutoTokenizer, TFAutoModelForSequenceClassification
#loading model
tokenizer = AutoTokenizer.from_pretrained("nimaafshar/parsbert-fa-sentiment-twitter")
  
model = TFAutoModelForSequenceClassification.from_pretrained("nimaafshar/parsbert-fa-sentiment-twitter")
classes = ["negative","neutral","positive"]
```
## Using Model
```python

#using model
sequences = [".غذا خیلی افتضاح بود متاسفم برای مدیریت رستورن خیلی بد بود.",
 "خیلی خوشمزده و عالی بود عالی",
"می‌تونم اسمتونو بپرسم؟"
]

for sequence in sequences:
  inputs = tokenizer(sequence, return_tensors="tf")
  classification_logits = model(inputs)[0]
  results = tf.nn.softmax(classification_logits, axis=1).numpy()[0]
  print(classes[np.argmax(results)])
  percentages = np.around(results*100)
  print(percentages)
```

note that this model is trained on persian corpus and is meant to be used on persian texts too.