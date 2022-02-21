---
language: en
tags:
- long context
- legal
pipeline_tag: fill-mask
---

# LSG model 
**Transformers >= 4.11.0**\
**This model relies on a custom modeling file, you need to add trust_remote_code=True**\
**See [\#13467](https://github.com/huggingface/transformers/pull/13467)**

* [Usage](#usage)
* [Parameters](#parameters)
* [Sparse selection type](#sparse-selection-type)
* [Tasks](#tasks)
* [Training global tokens](#training-global-tokens)
* [Conversion script](#conversion-script)

This model is adapted from [LEGAL-BERT](https://huggingface.co/nlpaueb/legal-bert-base-uncased) without additional pretraining yet. It uses the same number of parameters/layers and the same tokenizer.


This model can handle long sequences but faster and more efficiently than Longformer or BigBird (from Transformers) and relies on Local + Sparse + Global attention (LSG).


This model is "adaptive" and can handle a maximum length of 4096, short and long sequences are truncated if necessary. It is however recommended to feed 4096 long sequences since I did not test it extensively (padding="max_length", truncation=True). 



Support encoder-decoder but I didnt test it extensively.\
Implemented in PyTorch.

![attn](attn.png)

## Usage
The model relies on a custom modeling file, you need to add trust_remote_code=True to use it.

```python: 
from transformers import AutoModel, AutoTokenizer

model = AutoModel.from_pretrained("ccdv/legal-lsg-base-uncased-4096", trust_remote_code=True)
tokenizer = AutoTokenizer.from_pretrained("ccdv/legal-lsg-base-uncased-4096")
``` 

## Parameters
You can change various parameters like : 
* the number of global tokens (num_global_tokens=1)
* local block size (block_size=128)
* sparse block size (sparse_block_size=128)
* sparsity factor (sparsity_factor=2)
* see config.json file

Default parameters work well in practice. If you are short on memory, reduce block sizes, increase sparsity factor and remove dropout in the attention score matrix.

```python:
model = AutoModel.from_pretrained("ccdv/legal-lsg-base-uncased-4096", 
    trust_remote_code=True, 
    num_global_tokens=16,
    block_size=64,
    sparse_block_size=64,
    sparsity_factor=4,
    attention_probs_dropout_prob=0.0
)
``` 

## Sparse selection type

There are 3 different sparse selection patterns. The best type is task dependent. \
Note that for sequences with length < 2*block_size, the type has no effect.

* sparsity_type="norm", select highest norm tokens
    * Works best for a small sparsity_factor (2 to 4)
    * Additional parameters:
        * None
* sparsity_type="pooling", use average pooling to merge tokens
    * Works best for a small sparsity_factor (2 to 4)
    * Additional parameters:
        * None
* sparsity_type="lsh", use the LSH algorithm to cluster similar tokens
    * Works best for a large sparsity_factor (4+)
    * LSH relies on random projections, thus inference may differ slightly with different seeds
    * Additional parameters:
        * lsg_num_pre_rounds=1, pre merge tokens n times before computing centroids

## Tasks
Fill mask example:
```python:
from transformers import FillMaskPipeline, AutoModelForMaskedLM, AutoTokenizer

model = AutoModelForMaskedLM.from_pretrained("ccdv/legal-lsg-base-uncased-4096", trust_remote_code=True)
tokenizer = AutoTokenizer.from_pretrained("ccdv/legal-lsg-base-uncased-4096")

SENTENCES = ["Paris is the <mask> of France.", "The goal of life is <mask>."]
pipeline = FillMaskPipeline(model, tokenizer)
output = pipeline(SENTENCES, top_k=1)
    
output = [o[0]["sequence"] for o in output]
> ['Paris is the capital of France.', 'The goal of life is happiness.']
```


Classification example:
```python:
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("ccdv/legal-lsg-base-uncased-4096", 
    trust_remote_code=True, 
    pool_with_global=True, # pool with a global token instead of first token
)
tokenizer = AutoTokenizer.from_pretrained("ccdv/legal-lsg-base-uncased-4096")

SENTENCE = "This is a test for sequence classification. " * 300
token_ids = tokenizer(
    SENTENCE, 
    return_tensors="pt", 
    padding="max_length", # Optional but recommended
    truncation=True # Optional but recommended
    )
output = model(**token_ids)

> SequenceClassifierOutput(loss=None, logits=tensor([[-0.3051, -0.1762]], grad_fn=<AddmmBackward>), hidden_states=None, attentions=None)
```

## Training global tokens
To train global tokens and the classification head only:
```python:
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("ccdv/legal-lsg-base-uncased-4096", 
    trust_remote_code=True, 
    pool_with_global=True, # pool with a global token instead of first token
    num_global_tokens=16
)
tokenizer = AutoTokenizer.from_pretrained("ccdv/legal-lsg-base-uncased-4096")

for param in model.roberta.parameters():
    param.requires_grad = False
model.roberta.embeddings.global_embeddings.weight.requires_grad = True
```

## Conversion script

To convert a BERT or a RoBERTa checkpoint for LSG, see this [repo](https://github.com/ccdv-ai/convert_checkpoint_to_lsg).


**LEGAL-BERT**
```
@inproceedings{chalkidis-etal-2020-legal,
    title = "{LEGAL}-{BERT}: The Muppets straight out of Law School",
    author = "Chalkidis, Ilias  and
      Fergadiotis, Manos  and
      Malakasiotis, Prodromos  and
      Aletras, Nikolaos  and
      Androutsopoulos, Ion",
    booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2020",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    doi = "10.18653/v1/2020.findings-emnlp.261",
    pages = "2898--2904"
}
```

**Architecture**
```
@phdthesis{Condevaux2021,
  TITLE = {M{\'e}thodes d'apprentissage automatique pour l'analyse de corpus jurisprudentiels},
  AUTHOR = {Condevaux, Charles},
  SCHOOL = {{Universit{\'e} de N{\^i}mes}},
  YEAR = {2021},
}
```

Work in progress.