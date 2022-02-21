---
language: en

tags:
- sentence-embeddings
- sentence-similarity

### cambridgeltl/mirror-roberta-base-sentence
An unsupervised sentence encoder proposed by [Liu et al. (2021)](https://arxiv.org/pdf/2104.08027.pdf). The model is trained with unlabelled raw sentences, using [roberta-base](https://huggingface.co/roberta-base) as the base model. Please use `[CLS]` (before pooler) as the representation of the input.

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
