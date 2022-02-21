---
pipeline_tag: sentence-similarity
license: apache-2.0
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
---

# sentence-transformers/msmarco-bert-co-condensor

This is a port of the [Luyu/co-condenser-marco-retriever](https://huggingface.co/Luyu/co-condenser-marco-retriever) model to [sentence-transformers](https://www.SBERT.net) model: It maps sentences & paragraphs to a 768 dimensional dense vector space and is optimized for the task of semantic search.


It is based on the paper: [Unsupervised Corpus Aware Language Model Pre-training for Dense Passage Retrieval](https://arxiv.org/abs/2108.05540)


## Evaluation 



| Model | MS MARCO Dev (MRR@10) | TREC DL 2019 | TREC DL 2020 | FiQA (NDCG@10) | TREC COVID (NDCG@10) | TREC News (NDCG@10) | TREC Robust04 (NDCG@10) |
| ----- | :-------------------: | :----------: | :----------: | :------------: | :------------------: | :-----------------: | :--------------------: |
| [msmarco-roberta-base-ance-firstp](https://huggingface.co/sentence-transformers/msmarco-roberta-base-ance-firstp) | 33.01 | 67.84 | 66.04 | 29.5 | 67.12 | 38.2 | 39.2 |
| [msmarco-bert-co-condensor](https://huggingface.co/sentence-transformers/sentence-transformers/msmarco-bert-co-condensor) | 35.51 | 68.16 | 69.13 |26.04 | 66.89 | 28.54 | 30.71 |
| [msmarco-distilbert-base-tas-b](https://huggingface.co/sentence-transformers/msmarco-distilbert-base-tas-b) | 34.43 | 71.04 | 69.78 | 30.02 | 65.39 | 37.70 | 42.70 |
| [msmarco-distilbert-dot-v5](https://huggingface.co/sentence-transformers/msmarco-distilbert-dot-v5) | 37.25 | 70.14 | 71.08 | 28.61 | 71.96 | 37.88 | 38.29 | 
| [msmarco-bert-base-dot-v5](https://huggingface.co/sentence-transformers/msmarco-bert-base-dot-v5) | 38.08 | 70.51 | 73.45 | 32.29 | 74.81 | 38.81 | 42.67 | 



For more details on the comparison, see: [SBERT.net - MSMARCO Models](https://www.sbert.net/docs/pretrained-models/msmarco-v5.html)

In the paper, Gao & Callan claim a MS MARCO-Dev score of 38.2 (MRR@10). This is achieved by changing the benchmark: The orginal MS MARCO dataset just provides queries and text passages, from which you must retrieve the relevant passages for a given query.

In their [code](https://github.com/luyug/Dense/blob/454af38e06fe79aac8243b0fa31387c07ee874ab/examples/msmarco-passage-ranking/get_data.sh#L10), they combine the passages with the document titles from MS MARCO document task, i.e. they train and evaluate their model with additional information from a different benchmark. In the above table, the score of 35.41 (MRR@10) is on the MS MARCO Passages benchmark as it is proposed, without having the document titles.

They further trained their model with the document titles, which creates an information leackage: The document titles were re-constructed by the MS MARCO organizers at a later stage for the MS MARCO document benchmark. It was not possible to reconstruct all document titles for all passages. However, the distribution of having a title is not equal for relevant and non-relevant passages: 71.9% of the relevant passages have a document title, while only 64.4% of the non-relevant passages have a title. Hence, the model can learn that, as soon as there is a document title, the probability is higher that this passage is annotated as relevant. It will not make the decision based on the passage content, but by the artifact if there is a title or not.  

The information leackage and the change of the benchmark likely leads to the inflated scores reported in the paper.   
 

## Usage (Sentence-Transformers)

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer, util

query = "How many people live in London?"
docs = ["Around 9 Million people live in London", "London is known for its financial district"]

#Load the model
model = SentenceTransformer('sentence-transformers/msmarco-bert-co-condensor')

#Encode query and documents
query_emb = model.encode(query)
doc_emb = model.encode(docs)

#Compute dot score between query and all document embeddings
scores = util.dot_score(query_emb, doc_emb)[0].cpu().tolist()

#Combine docs & scores
doc_score_pairs = list(zip(docs, scores))

#Sort by decreasing score
doc_score_pairs = sorted(doc_score_pairs, key=lambda x: x[1], reverse=True)

#Output passages & scores
for doc, score in doc_score_pairs:
    print(score, doc)
```



## Usage (HuggingFace Transformers)
Without [sentence-transformers](https://www.SBERT.net), you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.

```python
from transformers import AutoTokenizer, AutoModel
import torch

#CLS Pooling - Take output from first token
def cls_pooling(model_output):
    return model_output.last_hidden_state[:,0]

#Encode text
def encode(texts):
    # Tokenize sentences
    encoded_input = tokenizer(texts, padding=True, truncation=True, return_tensors='pt')

    # Compute token embeddings
    with torch.no_grad():
        model_output = model(**encoded_input, return_dict=True)

    # Perform pooling
    embeddings = cls_pooling(model_output)

    return embeddings


# Sentences we want sentence embeddings for
query = "How many people live in London?"
docs = ["Around 9 Million people live in London", "London is known for its financial district"]

# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained("sentence-transformers/msmarco-bert-co-condensor")
model = AutoModel.from_pretrained("sentence-transformers/msmarco-bert-co-condensor")

#Encode query and docs
query_emb = encode(query)
doc_emb = encode(docs)

#Compute dot score between query and all document embeddings
scores = torch.mm(query_emb, doc_emb.transpose(0, 1))[0].cpu().tolist()

#Combine docs & scores
doc_score_pairs = list(zip(docs, scores))

#Sort by decreasing score
doc_score_pairs = sorted(doc_score_pairs, key=lambda x: x[1], reverse=True)

#Output passages & scores
for doc, score in doc_score_pairs:
    print(score, doc)
```



## Evaluation Results


For an automated evaluation of this model, see the *Sentence Embeddings Benchmark*: [https://seb.sbert.net](https://seb.sbert.net?model_name=sentence-transformers/msmarco-bert-co-condensor)


## Full Model Architecture
```
SentenceTransformer(
  (0): Transformer({'max_seq_length': 256, 'do_lower_case': False}) with Transformer model: DistilBertModel 
  (1): Pooling({'word_embedding_dimension': 768, 'pooling_mode_cls_token': True, 'pooling_mode_mean_tokens': False, 'pooling_mode_max_tokens': False, 'pooling_mode_mean_sqrt_len_tokens': False})
)
```

## Citing & Authors

Have a look at: [Unsupervised Corpus Aware Language Model Pre-training for Dense Passage Retrieval](https://arxiv.org/abs/2108.05540)