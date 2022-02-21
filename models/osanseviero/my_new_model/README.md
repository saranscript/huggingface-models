---
tags:
- sentence-transformers
- feature-extraction
---

# Name of Model

<!--- Describe your model here -->

## Model Description
The model consists of the following layers:

(0) Base Transformer Type: RobertaModel

(1) mean Pooling


## Usage (Sentence-Transformers)

Using this model becomes more convenient when you have [sentence-transformers](https://github.com/UKPLab/sentence-transformers) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["This is an example sentence"]

model = SentenceTransformer('model_name')
embeddings = model.encode(sentences)
print(embeddings)
```


## Usage (HuggingFace Transformers)

```python
from transformers import AutoTokenizer, AutoModel
import torch


#Mean Pooling - Take attention mask into account for correct averaging
def mean_pooling(model_output, attention_mask):
    token_embeddings = model_output[0] #First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    sum_embeddings = torch.sum(token_embeddings * input_mask_expanded, 1)
    sum_mask = torch.clamp(input_mask_expanded.sum(1), min=1e-9)
    return sum_embeddings / sum_mask


# Sentences we want sentence embeddings for
sentences = ['This is an example sentence']

# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained('model_name')
model = AutoModel.from_pretrained('model_name')

# Tokenize sentences
encoded_input = tokenizer(sentences, padding=True, truncation=True, max_length=128, return_tensors='pt')

# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)

# Perform pooling. In this case, max pooling.
sentence_embeddings = mean_pooling(model_output, encoded_input['attention_mask'])

print("Sentence embeddings:")
print(sentence_embeddings)
```



## Training Procedure

<!--- Describe how your model was trained -->

## Evaluation Results

<!--- Describe how your model was evaluated -->

## Citing & Authors

<!--- Describe where people can find more information -->
