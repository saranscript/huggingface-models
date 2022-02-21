# MatSciBERT
## A Materials Domain Language Model for Text Mining and Information Extraction

This is the pretrained model presented in [MatSciBERT: A Materials Domain Language Model for Text Mining and Information Extraction](https://arxiv.org/abs/2109.15290), which is a BERT model trained on material science research papers.

The training corpus comprises papers related to the broad category of materials: alloys, glasses, metallic glasses, cement and concrete. We have utilised the abstracts and full length of papers(when available). All the research papers have been downloaded from [ScienceDirect](https://www.sciencedirect.com/) using the [Elsevier API](https://dev.elsevier.com/). The detailed methodology is given in the paper.

The codes for pretraining and finetuning on downstream tasks are shared on [GitHub](https://github.com/m3rg-repo/MatSciBERT).

If you find this useful in your research, please consider citing:
```
@article{gupta_matscibert_2021,
  title = {{{MatSciBERT}}: A {{Materials Domain Language Model}} for {{Text Mining}} and {{Information Extraction}}},
  shorttitle = {{{MatSciBERT}}},
  author = {Gupta, Tanishq and Zaki, Mohd and Krishnan, N. M. Anoop and Mausam},
  year = {2021},
  month = sep,
  journal = {arXiv:2109.15290 [cond-mat]},
  eprint = {2109.15290},
  eprinttype = {arxiv},
  primaryclass = {cond-mat},
  archiveprefix = {arXiv},
  keywords = {Computer Science - Computation and Language,Condensed Matter - Materials Science}}
}
```