---
language: en

tags:
- sentence-embeddings
- sentence-similarity

### cambridgeltl/mirror-bert-base-uncased-sentence
An unsupervised sentence encoder proposed by [Liu et al. (2021)](https://arxiv.org/pdf/2104.08027.pdf). Trained with unlabelled raw sentences, using [bert-base-uncased](https://huggingface.co/bert-base-uncased) as the base model. Please use mean-pooling over *all tokens* (including padded ones) as the representation of the input.

Note the model does not replicate the exact numbers in the paper since the reported numbers in the paper are average of three runs.

### Citation
```bibtex
@inproceedings{
  liu2021fast,
  title={Fast, Effective, and Self-Supervised: Transforming Masked Language Models into Universal Lexical and Sentence Encoders},
  author={Liu, Fangyu and Vuli{\'c}, Ivan and Korhonen, Anna and Collier, Nigel},
  booktitle={EMNLP 2021},
  year={2021}
}
```
