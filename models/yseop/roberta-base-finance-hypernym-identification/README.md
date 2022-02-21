---
inference: false
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
---

<div style="clear: both;">
  <div style="float: left; margin-right 1em;">
    <h1><strong>FinISH (Finance-Identifying Sroberta for Hypernyms)</strong></h1>
  </div>
  <div>
    <h2><img src="https://pbs.twimg.com/profile_images/1333760924914753538/fQL4zLUw_400x400.png" alt="" width="25" height="25"></h2>
  </div>
  </div>
  
We present FinISH, a [SRoBERTa](https://huggingface.co/sentence-transformers/nli-roberta-base-v2) base model fine-tuned on the [FIBO ontology](https://spec.edmcouncil.org/fibo/) dataset for domain-specific representation learning on the [**Semantic Search**](https://www.sbert.net/examples/applications/semantic-search/README.html) downstream task.

## SRoBERTa Model Architecture
Sentence-RoBERTa (SRoBERTa) is a modification of the pretrained RoBERTa network that uses siamese and triplet network structures to derive semantically meaningful sentence embeddings that can be compared using cosine-similarity. This reduces the effort for finding the most similar pair from 65 hours with RoBERTa to about 5 seconds with SRoBERTa, while maintaining the accuracy from RoBERTa. SRoBERTa has been evaluated on common STS tasks and transfer learning tasks, where it outperforms other state-of-the-art sentence embeddings methods.

Paper: [Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks](https://arxiv.org/pdf/1908.10084.pdf).

Authors: *Nils Reimers and Iryna Gurevych*.

## Details on the downstream task (Semantic Search for Text Classification)
The objective of this task is to correctly classify a given term in the financial domain according to its prototypical hypernym in a list of available hypernyms:
* Bonds
* Forward
* Funds
* Future
* MMIs (Money Market Instruments)
* Option
* Stocks
* Swap
* Equity Index
* Credit Index
* Securities restrictions
* Parametric schedules
* Debt pricing and yields
* Credit Events
* Stock Corporation
* Central Securities Depository
* Regulatory Agency

This kind-based approach relies on identifying the closest hypernym semantically to the given term (even if they possess common properties with other hypernyms).

#### Data Description
The data is a scraped list of term definitions from the FIBO ontology website where each definition has been mapped to its closest hypernym from the proposed labels.
For multi-sentence definitions, we applied sentence-splitting by punctuation delimiters. We also applied lowercase transformation on all input data.

#### Data Instances
The dataset contains a label representing the hypernym of the given definition.
```json
{
  'label': 'bonds',
  'definition': 'callable convertible bond is a kind of callable bond, convertible bond.'
}
```

#### Data Fields
**label**: Can be one of the 17 predefined hypernyms.

**definition**: Financial term definition relating to a concept or object in the financial domain.

#### Data Splits
The data contains training data with **317101** entries.

#### Test set metrics
The representational learning model is evaluated on a representative test set with 20% of the entries. The test set is scored based on the following metrics:
* Average Accuracy
* Mean Rank (position of the correct label in a set of 5 model predictions)

We evaluate FinISH according to these metrics, where it outperforms other state-of-the-art sentence embeddings methods in this task.
* Average Accuracy: **0.73**
* Mean Rank: **1.61**

## Usage (Sentence-Transformers)
Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:
```
git clone https://github.com/huggingface/transformers.git
pip install -q ./transformers
pip install -U sentence-transformers
```
Then you can use the model like this:
```python
from sentence_transformers import SentenceTransformer, util
import torch
model = SentenceTransformer('yseop/roberta-base-finance-hypernym-identification')
# Our corpus containing the list of hypernym labels
hypernyms = ['Bonds',
\t\t\t'Forward',
\t\t\t'Funds',
\t\t\t'Future',
\t\t\t'MMIs',
\t\t\t'Option',
\t\t\t'Stocks',
\t\t\t'Swap',
\t\t\t'Equity Index',
\t\t\t'Credit Index',
\t\t\t'Securities restrictions',
\t\t\t'Parametric schedules',
\t\t\t'Debt pricing and yields',
\t\t\t'Credit Events',
\t\t\t'Stock Corporation',
\t\t\t'Central Securities Depository',
\t\t\t'Regulatory Agency']
hypernym_embeddings = model.encode(hypernyms, convert_to_tensor=True)
# Query sentences are financial terms to match to the predefined labels
queries = ['Convertible bond', 'weighted average coupon', 'Restriction 144-A']
# Find the closest 5 hypernyms of the corpus for each query sentence based on cosine similarity
top_k = min(5, len(hypernyms))
for query in queries:
    query_embedding = model.encode(query, convert_to_tensor=True)
    # We use cosine-similarity and torch.topk to find the highest 5 scores
    cos_scores = util.pytorch_cos_sim(query_embedding, hypernym_embeddings)[0]
    top_results = torch.topk(cos_scores, k=top_k)
    print("\
\
======================\
\
")
    print("Query:", query)
    print("\
Top 5 most similar hypernyms:")
    for score, idx in zip(top_results[0], top_results[1]):
        print(hypernyms[idx], "(Score: {:.4f})".format(score))
```
 
## Usage (HuggingFace Transformers)
Without [sentence-transformers](https://www.SBERT.net), you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.
```python
from transformers import AutoTokenizer, AutoModel
import torch
#Mean Pooling - Take attention mask into account for correct averaging
def mean_pooling(model_output, attention_mask):
    token_embeddings = model_output[0] #First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    return torch.sum(token_embeddings * input_mask_expanded, 1) / torch.clamp(input_mask_expanded.sum(1), min=1e-9)
# Query sentences are financial terms to match to the predefined labels
queries = ['Convertible bond', 'weighted average coupon', 'Restriction 144-A']
# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained('yseop/roberta-base-finance-hypernym-identification')
model = AutoModel.from_pretrained('yseop/roberta-base-finance-hypernym-identification')
# Tokenize sentences
encoded_input = tokenizer(queries, padding=True, truncation=True, return_tensors='pt')
# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)
# Perform pooling
query_embeddings = mean_pooling(model_output, encoded_input['attention_mask'])
print("Query embeddings:")
print(query_embeddings)
```

**Created by:** [Yseop](https://www.yseop.com/) | Pioneer in Natural Language Generation (NLG) technology. Scaling human expertise through Natural Language Generation.