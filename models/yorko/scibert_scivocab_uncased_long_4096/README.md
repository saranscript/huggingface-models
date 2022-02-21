# SciBERT Longformer

This is a Lonformer version of the [SciBERT uncased](https://huggingface.co/allenai/scibert_scivocab_uncased) model by Allen AI. The model is slower than SciBERT (~2.5x in my benchmarks) but can allow for 8x wider `max_seq_length` (4096 vs. 512) which is handy in case of working with long texts, e.g. scientific full texts. 

The conversion to Longformer was performed with a [tutorial](https://github.com/allenai/longformer/blob/master/scripts/convert_model_to_long.ipynb) by Allen AI: see a [Google Colab Notebook](https://colab.research.google.com/drive/1NPTnMkeAYOF2MWH3_uJYesuxxdOzxrFn?usp=sharing) by [Yury](https://yorko.github.io/) which closely follows the tutorial. 

Note: 

- no additional MLM pretraining of the Longformer was performed, the [collab notebook](https://colab.research.google.com/drive/1NPTnMkeAYOF2MWH3_uJYesuxxdOzxrFn?usp=sharing) stops at step 3, and step 4 is not done. The model can be improved with this additional MLM pretraining, better to do so with scientific texts, e.g. [S@ORC](https://github.com/allenai/s2orc), again by Allen AI. 
- no extensive benchmarks SciBERT Longformer vs. SciBERT were performed in terms of downstream task performance

Links:
 - the original [SciBERT repo](https://github.com/allenai/scibert)
 - the original [Longformer repo](https://github.com/allenai/longformer)


If using these models, please consider citing the following papers:
```
@inproceedings{beltagy-etal-2019-scibert,
    title = "SciBERT: A Pretrained Language Model for Scientific Text",
    author = "Beltagy, Iz  and Lo, Kyle  and Cohan, Arman",
    booktitle = "EMNLP",
    year = "2019",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/D19-1371"
}

@article{Beltagy2020Longformer,
  title={Longformer: The Long-Document Transformer},
  author={Iz Beltagy and Matthew E. Peters and Arman Cohan},
  journal={arXiv:2004.05150},
  year={2020},
}
```
