---

language:
- gl
- pt

widget:

- text: "A mesa estaba feita de [MASK]."

---

# BERT for Galician (Small)

This is a small pre-trained BERT model (6 layers, cased) for Galician (ILG/RAG spelling). It was evaluated on lexical semantics tasks, using a [dataset to identify homonymy and synonymy in context](https://github.com/marcospln/homonymy_acl21), and presented at ACL 2021.

There is also a base version (12 layers, cased): `marcosgg/bert-base-gl-cased`

## Citation
If you use this model, please cite the following [paper](https://arxiv.org/abs/2106.13553):

```
@inproceedings{garcia-2021-exploring,
    title = "Exploring the Representation of Word Meanings in Context: {A} Case Study on Homonymy and Synonymy",
    author = "Garcia, Marcos",
    booktitle = "Proceedings of the 59th Annual Meeting of the Association for Computational Linguistics and the 11th International Joint Conference on Natural Language Processing (Volume 1: Long Papers)",
    year = "2021",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.acl-long.281",
    doi = "10.18653/v1/2021.acl-long.281",
    pages = "3625--3640"
}
```
