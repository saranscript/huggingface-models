---
language: "en"
tags:
- dpr
- dense-passage-retrieval
- knowledge-distillation
datasets:
- ms_marco
---

# Margin-MSE Trained DistilBert for Dense Passage Retrieval

We provide a retrieval trained DistilBert-based model (we call the architecture BERT_Dot). Our model is trained with Margin-MSE using a 3 teacher BERT_Cat (concatenated BERT scoring) ensemble on MSMARCO-Passage.

This instance can be used to **re-rank a candidate set** or **directly for a vector index based dense retrieval**. The architecture is a 6-layer DistilBERT, without architecture additions or modifications (we only change the weights during training) - to receive a query/passage representation we pool the CLS vector. We use the same BERT layers for both query and passage encoding (yields better results, and lowers memory requirements).

If you want to know more about our simple, yet effective knowledge distillation method for efficient information retrieval models for a variety of student architectures that is used for this model instance check out our paper: https://arxiv.org/abs/2010.02666 🎉

For more information, training data, source code, and a minimal usage example please visit: https://github.com/sebastian-hofstaetter/neural-ranking-kd

## Effectiveness on MSMARCO Passage & TREC-DL'19

We trained our model on the MSMARCO standard ("small"-400K query) training triples with knowledge distillation with a batch size of 32 on a single consumer-grade GPU (11GB memory).

For re-ranking we used the top-1000 BM25 results.

### MSMARCO-DEV

|                                  | MRR@10 | NDCG@10 | Recall@1K                   |
|----------------------------------|--------|---------|-----------------------------|
| BM25                             | .194   | .241    | .868  |
| **Margin-MSE BERT_Dot** (Re-ranking) | .332   | .391    | .868 (from BM25 candidates) |
| **Margin-MSE BERT_Dot** (Retrieval)  | .323   | .381    | .957                        |

### TREC-DL'19

For MRR and Recall we use the recommended binarization point of the graded relevance of 2. This might skew the results when compared to other binarization point numbers.

|                                  | MRR@10 | NDCG@10 | Recall@1K                   |
|----------------------------------|--------|---------|-----------------------------|
| BM25                             | .689   | .501    | .739  |
| **Margin-MSE BERT_Dot** (Re-ranking) | .862   | .712    | .739 (from BM25 candidates) |
| **Margin-MSE BERT_Dot** (Retrieval)  | .868   | .697    | .769                        |

For more baselines, info and analysis, please see the paper: https://arxiv.org/abs/2010.02666

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