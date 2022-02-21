---
language: fa
license: apache-2.0
---

# ALBERT Persian

A Lite BERT for Self-supervised Learning of Language Representations for the Persian Language

> میتونی بهش بگی برت_کوچولو

[ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) is the first attempt on ALBERT for the Persian Language. The model was trained based on Google's ALBERT BASE Version 2.0 over various writing styles from numerous subjects (e.g., scientific, novels, news) with more than 3.9M documents, 73M sentences, and 1.3B words, like the way we did for ParsBERT.

Please follow the [ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) repo for the latest information about previous and current models.

## Persian Sentiment [Digikala, SnappFood, DeepSentiPers]

It aims to classify text, such as comments, based on their emotional bias. We tested three well-known datasets for this task: `Digikala` user comments, `SnappFood` user comments, and `DeepSentiPers` in two binary-form and multi-form types.


### DeepSentiPers

which is a balanced and augmented version of SentiPers, contains 12,138 user opinions about digital products labeled with five different classes; two positives (i.e., happy and delighted), two negatives (i.e., furious and angry) and one neutral class. Therefore, this dataset can be utilized for both multi-class and binary classification. In the case of binary classification, the neutral class and its corresponding sentences are removed from the dataset.

**Binary:**
1. Negative (Furious + Angry)
2. Positive (Happy + Delighted)

**Multi**
1. Furious
2. Angry
3. Neutral
4. Happy
5. Delighted


|   Label   |   #  |
|:---------:|:----:|
|  Furious  |  236 |
|   Angry   | 1357 |
|  Neutral  | 2874 |
|   Happy   | 2848 |
| Delighted | 2516 |


**Download**
You can download the dataset from:

- [SentiPers](https://github.com/phosseini/sentipers)
- [DeepSentiPers](https://github.com/JoyeBright/DeepSentiPers)


## Results

The following table summarizes the F1 score obtained as compared to other models and architectures.

|          Dataset         | ALBERT-fa-base-v2 | ParsBERT-v1 | mBERT | DeepSentiPers |
|:------------------------:|:-----------------:|:-----------:|:-----:|:-------------:|
|  SentiPers (Multi Class) |       66.12       |    71.11    |   -   |     69.33     |
| SentiPers (Binary Class) |       91.09       |    92.13    |   -   |     91.98     |


### BibTeX entry and citation info

Please cite in publications as the following:

```bibtex
@misc{ALBERTPersian,
  author = {Mehrdad Farahani},
  title = {ALBERT-Persian: A Lite BERT for Self-supervised Learning of Language Representations for the Persian Language},
  year = {2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/m3hrdadfi/albert-persian}},
}

@article{ParsBERT,
    title={ParsBERT: Transformer-based Model for Persian Language Understanding},
    author={Mehrdad Farahani, Mohammad Gharachorloo, Marzieh Farahani, Mohammad Manthouri},
    journal={ArXiv},
    year={2020},
    volume={abs/2005.12515}
}
```

## Questions?
Post a Github issue on the [ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) repo.