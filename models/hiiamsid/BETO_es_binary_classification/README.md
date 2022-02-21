---
language:
- es
tags:
- es
- ticket classification
license: "apache-2.0"
datasets:
- self made to classify whether text is related to technology or not.
metrics:
- fscore
- accuracy
- precision
- recall
---
# BETO(cased)
This model was built using pytorch.
## Model description
Input for the model: Any spanish text
Output for the model: Sentiment. (0 - Negative, 1 - Positive(i.e. technology relate))
#### How to use
Here is how to use this model to get the features of a given text in *PyTorch*:
```python
# You can include sample code which will be formatted
from transformers import AutoTokenizer, AutoModelForSequenceClassification
tokenizer = AutoTokenizer.from_pretrained("hiiamsid/BETO_es_binary_classification")
model = AutoModelForSequenceClassification.from_pretrained("hiiamsid/BETO_es_binary_classification")
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```
## Training procedure
I trained on the dataset on the [dccuchile/bert-base-spanish-wwm-cased](https://huggingface.co/dccuchile/bert-base-spanish-wwm-cased).
