---
tags:
- summarization
- pegasus
- long context
language:
- en
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
* [Conversion script](#conversion-script)

This model is adapted from [Pegasus-large](https://huggingface.co/google/pegasus-large) for encoder-decoder tasks without additional pretraining. It uses the same number of parameters/layers and the same tokenizer.


This model can handle long sequences but faster and more efficiently than Longformer (LED) or BigBird (Pegasus) from the hub and relies on Local + Sparse + Global attention (LSG).


This model is "adaptive" and can handle a maximum length of 4096, short and long sequences are truncated if necessary. It is however recommended to feed 4096 long sequences since I did not test it extensively (padding="max_length", truncation=True). 

Implemented in PyTorch.

![attn](attn.png)

## Usage
The model relies on a custom modeling file, you need to add trust_remote_code=True to use it.

```python: 
from transformers import AutoModel, AutoTokenizer

model = AutoModel.from_pretrained("ccdv/lsg-pegasus-large-4096", trust_remote_code=True)
tokenizer = AutoTokenizer.from_pretrained("ccdv/lsg-pegasus-large-4096")
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
model = AutoModel.from_pretrained("ccdv/lsg-pegasus-large-4096", 
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
Seq2Seq example for summarization:
```python:
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer

model = AutoModelForSeq2SeqLM.from_pretrained("ccdv/lsg-pegasus-large-4096", 
    trust_remote_code=True, 
    pass_global_tokens_to_decoder=True, # Pass encoder global tokens to decoder
)
tokenizer = AutoTokenizer.from_pretrained("ccdv/lsg-pegasus-large-4096")

SENTENCE = "This is a test sequence to test the model. " * 300
token_ids = tokenizer(
    SENTENCE, 
    return_tensors="pt", 
    padding="max_length", # Optional but recommended
    truncation=True # Optional but recommended
    )
output = model(**token_ids)
```


Classification example:
```python:
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("ccdv/lsg-pegasus-large-4096", 
    trust_remote_code=True, 
    pass_global_tokens_to_decoder=True, # Pass encoder global tokens to decoder
)
tokenizer = AutoTokenizer.from_pretrained("ccdv/lsg-pegasus-large-4096")

SENTENCE = "This is a test sequence to test the model. " * 300
token_ids = tokenizer(
    SENTENCE, 
    return_tensors="pt", 
    padding="max_length", # Optional but recommended
    truncation=True # Optional but recommended
    )
output = model(**token_ids)

> SequenceClassifierOutput(loss=None, logits=tensor([[-0.3051, -0.1762]], grad_fn=<AddmmBackward>), hidden_states=None, attentions=None)
```


## Conversion script

To convert a BERT, RoBERTa or BART checkpoint to LSG, see this [repo](https://github.com/ccdv-ai/convert_checkpoint_to_lsg).


**Pegasus**
```
@misc{zhang2019pegasus,
    title={PEGASUS: Pre-training with Extracted Gap-sentences for Abstractive Summarization},
    author={Jingqing Zhang and Yao Zhao and Mohammad Saleh and Peter J. Liu},
    year={2019},
    eprint={1912.08777},
    archivePrefix={arXiv},
    primaryClass={cs.CL}
}
```

**LSG Architecture**
```
@phdthesis{Condevaux2021,
  TITLE = {M{\'e}thodes d'apprentissage automatique pour l'analyse de corpus jurisprudentiels},
  AUTHOR = {Condevaux, Charles},
  SCHOOL = {{Universit{\'e} de N{\^i}mes}},
  YEAR = {2021},
}
```

Work in progress.