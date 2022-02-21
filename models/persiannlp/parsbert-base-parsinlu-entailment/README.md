---
language:
- fa
- multilingual
thumbnail: https://upload.wikimedia.org/wikipedia/commons/a/a2/Farsi.svg
tags:
- entailment
- parsbert
- persian
- farsi
license: cc-by-nc-sa-4.0
datasets:
- parsinlu
metrics:
- accuracy
---

# Textual Entailment (مدل برای پاسخ به استلزام منطقی)

This is a model for textual entailment problems. 
Here is an example of how you can run this model: 

```python 
import torch
from transformers import AutoModelForSequenceClassification, AutoTokenizer
import numpy as np

labels = ["entails", "contradicts", "neutral"]
model_name_or_path = "persiannlp/parsbert-base-parsinlu-entailment"
model = AutoModelForSequenceClassification.from_pretrained(model_name_or_path)
tokenizer = AutoTokenizer.from_pretrained(model_name_or_path,)


def model_predict(text_a, text_b):
    features = tokenizer( [(text_a, text_b)], padding="max_length", truncation=True, return_tensors='pt')
    output = model(**features)
    logits = output[0]
    probs = torch.nn.functional.softmax(logits, dim=1).tolist()
    idx = np.argmax(np.array(probs))
    print(labels[idx], probs)


model_predict(
    "این مسابقات بین آوریل و دسامبر در هیپودروم ولیفندی در نزدیکی باکرکی ، ۱۵ کیلومتری (۹ مایل) غرب استانبول برگزار می شود.",
    "در ولیفندی هیپودروم، مسابقاتی از آوریل تا دسامبر وجود دارد."
)

model_predict(
"آیا کودکانی وجود دارند که نیاز به سرگرمی دارند؟",
    "هیچ کودکی هرگز نمی خواهد سرگرم شود.",
)

model_predict(
    "ما به سفرهایی رفته ایم که در نهرهایی شنا کرده ایم",
    "علاوه بر استحمام در نهرها ، ما به اسپا ها و سونا ها نیز رفته ایم."
)
```


For more details, visit this page: https://github.com/persiannlp/parsinlu/ 
