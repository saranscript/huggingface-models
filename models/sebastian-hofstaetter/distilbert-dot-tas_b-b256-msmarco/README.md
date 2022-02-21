---
language: "en"
tags:
- dpr
- dense-passage-retrieval
- knowledge-distillation
datasets:
- ms_marco
---

# DistilBert for Dense Passage Retrieval trained with Balanced Topic Aware Sampling (TAS-B)

We provide a retrieval trained DistilBert-based model (we call the *dual-encoder then dot-product scoring* architecture BERT_Dot) trained with Balanced Topic Aware Sampling on MSMARCO-Passage.

This instance was trained with a batch size of 256 and can be used to **re-rank a candidate set** or **directly for a vector index based dense retrieval**. The architecture is a 6-layer DistilBERT, without architecture additions or modifications (we only change the weights during training) - to receive a query/passage representation we pool the CLS vector. We use the same BERT layers for both query and passage encoding (yields better results, and lowers memory requirements).

If you want to know more about our efficient (can be done on a single consumer GPU in 48 hours) batch composition procedure and dual supervision for dense retrieval training, check out our paper: https://arxiv.org/abs/2104.06967 🎉

For more information and a minimal usage example please visit: https://github.com/sebastian-hofstaetter/tas-balanced-dense-retrieval

## Effectiveness on MSMARCO Passage & TREC-DL'19

We trained our model on the MSMARCO standard ("small"-400K query) training triples re-sampled with our TAS-B method. As teacher models we used the BERT_CAT pairwise scores as well as the ColBERT model for in-batch-negative signals published here: https://github.com/sebastian-hofstaetter/neural-ranking-kd

### MSMARCO-DEV (7K)

|                                  | MRR@10 | NDCG@10 | Recall@1K                   |
|----------------------------------|--------|---------|-----------------------------|
| BM25                             | .194   | .241    | .857  |
| **TAS-B BERT_Dot** (Retrieval)   | .347   | .410    | .978                        |

### TREC-DL'19

For MRR and Recall we use the recommended binarization point of the graded relevance of 2. This might skew the results when compared to other binarization point numbers.

|                                  | MRR@10 | NDCG@10 | Recall@1K                   |
|----------------------------------|--------|---------|-----------------------------|
| BM25                             | .689   | .501    | .739  |
| **TAS-B BERT_Dot** (Retrieval)   | .883   | .717    | .843                       |

### TREC-DL'20

For MRR and Recall we use the recommended binarization point of the graded relevance of 2. This might skew the results when compared to other binarization point numbers.

|                                  | MRR@10 | NDCG@10 | Recall@1K                   |
|----------------------------------|--------|---------|-----------------------------|
| BM25                             | .649   | .475    | .806  |
| **TAS-B BERT_Dot** (Retrieval)   | .843   | .686    | .875                        |


For more baselines, info and analysis, please see the paper: https://arxiv.org/abs/2104.06967

## Limitations & Bias

- The model inherits social biases from both DistilBERT and MSMARCO. 

- The model is only trained on relatively short passages of MSMARCO (avg. 60 words length), so it might struggle with longer text. 


## Citation

If you use our model checkpoint please cite our work as:

```
@inproceedings{Hofstaetter2021_tasb_dense_retrieval,
 author = {Sebastian Hofst{\"a}tter and Sheng-Chieh Lin and Jheng-Hong Yang and Jimmy Lin and Allan Hanbury},
 title = {{Efficiently Teaching an Effective Dense Retriever with Balanced Topic Aware Sampling}},
 booktitle = {Proc. of SIGIR},
 year = {2021},
}
```