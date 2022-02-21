# TinyBERT_L-4_H-312_v2 English Sentence Encoder

This is distilled from the `bert-base-nli-stsb-mean-tokens` pre-trained model from [Sentence-Transformers](https://sbert.net/).

The embedding vector is obtained by mean/average pooling of the last layer's hidden states.

Update 20210325: Added the attention matrices imitation objective as in the TinyBERT paper, and the distill target has been changed from `distilbert-base-nli-stsb-mean-tokens` to `bert-base-nli-stsb-mean-tokens` (they have almost the same STSb performance).

## Model Comparison

We compute cosine similarity scores of the embeddings of the sentence pair to get the spearman correlation on the STS benchmark (bigger is better):

|                                      | Dev   | Test  |
| ------------------------------------ | ----- | ----- |
| bert-base-nli-stsb-mean-tokens       | .8704 | .8505 |
| distilbert-base-nli-stsb-mean-tokens | .8667 | .8516 |
| TinyBERT_L-4_H-312_v2-distill-AllNLI | .8587 | .8283 |
| TinyBERT_L-4_H (20210325)            | .8551 | .8341 |
