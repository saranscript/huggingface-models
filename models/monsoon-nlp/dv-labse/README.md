---
language: dv
---

# dv-labse

This is an experiment in cross-lingual transfer learning, to insert Dhivehi word and
word-piece tokens into Google's LaBSE model.

- Original model weights: https://huggingface.co/setu4993/LaBSE
- Original model announcement: https://ai.googleblog.com/2020/08/language-agnostic-bert-sentence.html

This currently outperforms dv-wave and dv-MuRIL (a similar transfer learning model) on 
the Maldivian News Classification task https://github.com/Sofwath/DhivehiDatasets

- mBERT: 52%
- dv-wave (ELECTRA): 89%
- dv-muril: 90.7%
- dv-labse: 91.3-91.5% (may continue training)

## Training

- Start with LaBSE (similar to mBERT) with no Thaana vocabulary
- Based on PanLex dictionaries, attach 1,100 Dhivehi words to Sinhalese or English embeddings
- Add remaining words and word-pieces from dv-wave's vocabulary to vocab.txt
- Continue BERT pretraining on Dhivehi text

CoLab notebook: 
https://colab.research.google.com/drive/1CUn44M2fb4Qbat2pAvjYqsPvWLt1Novi
