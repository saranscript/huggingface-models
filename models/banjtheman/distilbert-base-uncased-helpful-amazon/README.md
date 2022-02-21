---
license: apache-2.0
---

## Overview

This model was trained with data from https://registry.opendata.aws/helpful-sentences-from-reviews/ to predict how "helpful" a review is.

The model was fine-tuned from the `distilbert-base-uncased` model

### Labels
LABEL_0 - Not helpful  
LABEL_1 - Helpful  

### How to use

The following code shows how to make a prediction with this model

```python
from transformers import (
    AutoTokenizer,
    AutoModelForSequenceClassification,
    TextClassificationPipeline,
)

tokenizer = AutoTokenizer.from_pretrained("banjtheman/distilbert-base-uncased-helpful-amazon")

model = AutoModelForSequenceClassification.from_pretrained(
    "banjtheman/distilbert-base-uncased-helpful-amazon"
)

pipe = TextClassificationPipeline(model=model, tokenizer=tokenizer)

result = pipe("This was a Christmas gift for my grandson.")

print(result)

#[{'label': 'LABEL_0', 'score': 0.998775064945221}]
# This is NOT A HELPFUL comment

```