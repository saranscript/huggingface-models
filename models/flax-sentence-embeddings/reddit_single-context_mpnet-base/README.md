---
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
language: en
---

# Model description

The project aims to train sentence embedding models on very large sentence level datasets using a self-supervised 
contrastive learning objective. We used the pretrained ['mpnet-base'](https://huggingface.co/microsoft/mpnet-base) model and fine-tuned in on a 
700M sentence pairs dataset. We use a contrastive learning objective: given a sentence from the pair, the model should predict which out of a set of randomly sampled other sentences, was actually paired with it in our dataset.

We developped this model during the 
[Community week using JAX/Flax for NLP & CV](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), 
organized by Hugging Face. We developped this model as part of the project:
[Train the Best Sentence Embedding Model Ever with 1B Training Pairs](https://discuss.huggingface.co/t/train-the-best-sentence-embedding-model-ever-with-1b-training-pairs/7354). We benefited from efficient hardware infrastructure to run the project: 7 TPUs v3-8, as well
as intervention from Google’s Flax, JAX, and Cloud team member about efficient deep learning frameworks.

## Intended uses

Our model is intented to be used as a sentence encoder. Given an input sentence, it ouptuts a vector which captures 
the sentence semantic information. The sentence vector may be used for information retrieval, clustering or sentence 
similarity tasks.

## How to use

Here is how to use this model to get the features of a given text using [SentenceTransformers](https://github.com/UKPLab/sentence-transformers) library:

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer('flax-sentence-embeddings/reddit_single-context_mpnet-base')
text = "Replace me by any text you'd like."
text_embbedding = model.encode(text)
# array([-0.01559514,  0.04046123,  0.1317083 ,  0.00085931,  0.04585106,
#        -0.05607086,  0.0138078 ,  0.03569756,  0.01420381,  0.04266302 ...],
#        dtype=float32)
```

# Training procedure

## Pre-training 

We use the pretrained ['mpnet-base'](https://huggingface.co/microsoft/mpnet-base). 
Please refer to the model card for more detailed information about the pre-training procedure.

## Fine-tuning 

We fine-tune the model using a contrastive objective. Formally, we compute the cosine similarity from each possible sentence pairs from the batch.
We then apply the cross entropy loss by comparing with true pairs.

### Hyper parameters

We trained ou model on a TPU v3-8. We train the model during 540k steps using a batch size of 1024 (128 per TPU core).
We use a learning rate warm up of 500. The sequence length was limited to 128 tokens. We used the AdamW optimizer with
a 2e-5 learning rate. The full training script is accessible in this current repository.

### Training data

We use the concatenation from multiple datasets to fine-tune our model. The total number of sentence pairs is above 700M sentences.
We sampled each dataset given a weighted probability which configuration is detailed in the `data_config.json` file.
We only use the first context response when building the dataset.


| Dataset                                                  | Paper                                    | Number of training tuples  |
|:--------------------------------------------------------:|:----------------------------------------:|:--------------------------:|
| [Reddit conversationnal](https://github.com/PolyAI-LDN/conversational-datasets/tree/master/reddit) | [paper](https://arxiv.org/abs/1904.06472) | 726,484,430 |
