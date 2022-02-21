---
pipeline_tag: feature-extraction
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
---

# Sentence Embeddings with `bert-zwnj-wnli-mean-tokens`

## Usage (Sentence-Transformers)
Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer


sentences = [
    'اولین حکمران شهر بابل کی بود؟',
    'در فصل زمستان چه اتفاقی افتاد؟',
    'میراث کوروش'
]
model = SentenceTransformer('m3hrdadfi/bert-zwnj-wnli-mean-tokens')
embeddings = model.encode(sentences)
print(embeddings)
```

## Usage (HuggingFace Transformers)
Without [sentence-transformers](https://www.SBERT.net), you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.

```python
from transformers import AutoTokenizer, AutoModel
import torch


# Max Pooling - Take the max value over time for every dimension. 
def max_pooling(model_output, attention_mask):
    token_embeddings = model_output[0] #First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    token_embeddings[input_mask_expanded == 0] = -1e9  # Set padding tokens to large negative value
    return torch.mean(token_embeddings, 1)[0]

# Sentences we want sentence embeddings for
sentences = [
    'اولین حکمران شهر بابل کی بود؟',
    'در فصل زمستان چه اتفاقی افتاد؟',
    'میراث کوروش'
]

# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained('m3hrdadfi/bert-zwnj-wnli-mean-tokens')
model = AutoModel.from_pretrained('m3hrdadfi/bert-zwnj-wnli-mean-tokens')

# Tokenize sentences
encoded_input = tokenizer(sentences, padding=True, truncation=True, return_tensors='pt')
# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)
# Perform pooling. In this case, max pooling.
sentence_embeddings = max_pooling(model_output, encoded_input['attention_mask'])

print("Sentence embeddings:")
print(sentence_embeddings)
```

## Questions?
Post a Github issue from [HERE](https://github.com/m3hrdadfi/sentence-transformers).