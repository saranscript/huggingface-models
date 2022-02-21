---
language: "en"
tags:
- re-ranking
- passage-ranking
- knowledge-distillation
datasets:
- ms_marco
---

# Margin-MSE Trained DistilBERT-Cat (vanilla/mono/concatenated DistilBERT re-ranker)

We provide a retrieval trained DistilBERT-Cat model. Our model is trained with Margin-MSE using a 3 teacher BERT_Cat (concatenated BERT scoring) ensemble on MSMARCO-Passage.

This instance can be used to **re-rank a candidate set**. The architecure is a 6-layer DistilBERT, with an additional single linear layer at the end.

If you want to know more about our simple, yet effective knowledge distillation method for efficient information retrieval models for a variety of student architectures that is used for this model instance check out our paper: https://arxiv.org/abs/2010.02666 🎉

For more information, training data, source code, and a minimal usage example please visit: https://github.com/sebastian-hofstaetter/neural-ranking-kd

## Configuration

- fp16 trained, so fp16 inference shouldn't be a problem

## Model Code

````python
from transformers import AutoTokenizer,AutoModel, PreTrainedModel,PretrainedConfig
from typing import Dict
import torch

class BERT_Cat_Config(PretrainedConfig):
    model_type = "BERT_Cat"
    bert_model: str
    trainable: bool = True

class BERT_Cat(PreTrainedModel):
    """
    The vanilla/mono BERT concatenated (we lovingly refer to as BERT_Cat) architecture 
    -> requires input concatenation before model, so that batched input is possible
    """
    config_class = BERT_Cat_Config
    base_model_prefix = "bert_model"

    def __init__(self,
                 cfg) -> None:
        super().__init__(cfg)
        
        self.bert_model = AutoModel.from_pretrained(cfg.bert_model)

        for p in self.bert_model.parameters():
            p.requires_grad = cfg.trainable

        self._classification_layer = torch.nn.Linear(self.bert_model.config.hidden_size, 1)

    def forward(self,
                query_n_doc_sequence):

        vecs = self.bert_model(**query_n_doc_sequence)[0][:,0,:] # assuming a distilbert model here
        score = self._classification_layer(vecs)
        return score

tokenizer = AutoTokenizer.from_pretrained("distilbert-base-uncased") # honestly not sure if that is the best way to go, but it works :)
model = BERT_Cat.from_pretrained("sebastian-hofstaetter/distilbert-cat-margin_mse-T2-msmarco")
````

## Effectiveness on MSMARCO Passage & TREC Deep Learning '19

We trained our model on the MSMARCO standard ("small"-400K query) training triples with knowledge distillation with a batch size of 32 on a single consumer-grade GPU (11GB memory).

For re-ranking we used the top-1000 BM25 results.

### MSMARCO-DEV

Here, we use the larger 49K query DEV set (same range as the smaller 7K DEV set, minimal changes possible)

|                                  | MRR@10 | NDCG@10 |
|----------------------------------|--------|---------|
| BM25                             | .194   | .241    |
| **Margin-MSE DistilBERT_Cat** (Re-ranking) | .391   | .451   |

### TREC-DL'19

For MRR we use the recommended binarization point of the graded relevance of 2. This might skew the results when compared to other binarization point numbers.

|                                  | MRR@10 | NDCG@10 |
|----------------------------------|--------|---------|
| BM25                             | .689   | .501    |
| **Margin-MSE DistilBERT_Cat** (Re-ranking) | .891   | .747    |

For more metrics, baselines, info and analysis, please see the paper: https://arxiv.org/abs/2010.02666

## Limitations & Bias

- The model inherits social biases from both DistilBERT and MSMARCO. 

- The model is only trained on relatively short passages of MSMARCO (avg. 60 words length), so it might struggle with longer text. 


## Citation

If you use our model checkpoint please cite our work as:

```
@misc{hofstaetter2020_crossarchitecture_kd,
      title={Improving Efficient Neural Ranking Models with Cross-Architecture Knowledge Distillation}, 
      author={Sebastian Hofst{\"a}tter and Sophia Althammer and Michael Schr{\"o}der and Mete Sertkan and Allan Hanbury},
      year={2020},
      eprint={2010.02666},
      archivePrefix={arXiv},
      primaryClass={cs.IR}
}
```