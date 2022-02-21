---
language: dv
---

# dv-muril

This is an experiment in transfer learning, to insert Dhivehi word and
word-piece tokens into Google's MuRIL model.

This BERT-based model currently performs better than dv-wave ELECTRA on
the Maldivian News Classification task https://github.com/Sofwath/DhivehiDatasets

## Training

- Start with MuRIL (similar to mBERT) with no Thaana vocabulary
- Based on PanLex dictionaries, attach 1,100 Dhivehi words to Malayalam or English embeddings
- Add remaining words and word-pieces from BertWordPieceTokenizer / vocab.txt
- Continue BERT pretraining

## Performance

- mBERT: 52%
- dv-wave (ELECTRA, 30k vocab): 89%
- dv-muril (10k vocab) before BERT pretraining step: 89.8%
- previous dv-muril (30k vocab): 90.7%
- dv-muril (10k vocab): 91.6%

CoLab notebook: 
https://colab.research.google.com/drive/113o6vkLZRkm6OwhTHrvE0x6QPpavj0fn
