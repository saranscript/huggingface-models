ArabicTransformer Large model (B8-8-8 with decoder)

<b>Paper</b> : ArabicTransformer: Efficient Large Arabic Language Model with Funnel Transformer and ELECTRA Objective (EMNLP21)

<b>Abstract</b>

Pre-training Transformer-based models such as BERT and ELECTRA on a collection of Arabic corpora, demonstrated by both AraBERT and AraELECTRA, shows an impressive result on downstream tasks. However, pre-training Transformer-based language models is computationally expensive, especially for large-scale models. Recently, Funnel Transformer has addressed the sequential redundancy inside Transformer architecture by compressing the sequence of hidden states, leading to a significant reduction in the pretraining cost. This paper empirically studies the performance and efficiency of building an Arabic language model with Funnel Transformer and ELECTRA objective. We find that our model achieves state-of-the-art results on several Arabic downstream tasks despite using less computational resources compared to other BERT-based models.

<b>Description</b> 

This model was pre-trained on 44GB of Arabic corpora using [Funnel Transformer with ELECTRA objective](https://arxiv.org/abs/2006.03236). We will update you with more details about the model and our accepted paper later at EMNLP21. Check our GitHub page for the latest updates and examples: https://github.com/salrowili/ArabicTransformer

```bibtex
@inproceedings{alrowili-shanker-2021-arabictransformer-efficient,
    title = "{A}rabic{T}ransformer: Efficient Large {A}rabic Language Model with Funnel Transformer and {ELECTRA} Objective",
    author = "Alrowili, Sultan  and
      Shanker, Vijay",
    booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2021",
    month = nov,
    year = "2021",
    address = "Punta Cana, Dominican Republic",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.findings-emnlp.108",
    pages = "1255--1261",
    abstract = "Pre-training Transformer-based models such as BERT and ELECTRA on a collection of Arabic corpora, demonstrated by both AraBERT and AraELECTRA, shows an impressive result on downstream tasks. However, pre-training Transformer-based language models is computationally expensive, especially for large-scale models. Recently, Funnel Transformer has addressed the sequential redundancy inside Transformer architecture by compressing the sequence of hidden states, leading to a significant reduction in the pre-training cost. This paper empirically studies the performance and efficiency of building an Arabic language model with Funnel Transformer and ELECTRA objective. We find that our model achieves state-of-the-art results on several Arabic downstream tasks despite using less computational resources compared to other BERT-based models.",
}
```