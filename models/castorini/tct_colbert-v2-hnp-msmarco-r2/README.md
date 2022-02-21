This model is to reproduce a variant of TCT-ColBERT-V2 dense retrieval models described in the following paper:
> Sheng-Chieh Lin, Jheng-Hong Yang, and Jimmy Lin. [In-Batch Negatives for Knowledge Distillation with Tightly-CoupledTeachers for Dense Retrieval.](https://cs.uwaterloo.ca/~jimmylin/publications/Lin_etal_2021_RepL4NLP.pdf) _RepL4NLP 2021_.

Specifically, this checkpoint is finetuned for MS MARCO-V2 passage ranking, and we use this checkpoint as our ``trained'' model for TREC DL 2021 submissions.
The initial checkpoint is from a previous one [tct_colbert-v2-hnp-msmarco](https://huggingface.co/castorini/tct_colbert-v2-hnp-msmarco) trained on [MS MARCO](https://github.com/microsoft/MSMARCO-Passage-Ranking).
For fine-tuning, we construct our training data for MS MARCO-V2 passage ranking using this [script](https://github.com/castorini/pyserini/blob/master/scripts/msmarco_v2/generate_train_triplet.py).

