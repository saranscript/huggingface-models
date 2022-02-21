---
language: fa
license: apache-2.0
---

# ALBERT Persian

A Lite BERT for Self-supervised Learning of Language Representations for the Persian Language

> میتونی بهش بگی برت_کوچولو

[ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) is the first attempt on ALBERT for the Persian Language. The model was trained based on Google's ALBERT BASE Version 2.0 over various writing styles from numerous subjects (e.g., scientific, novels, news) with more than 3.9M documents, 73M sentences, and 1.3B words, like the way we did for ParsBERT.

Please follow the [ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) repo for the latest information about previous and current models.

## Persian Text Classification [DigiMag, Persian News]

The task target is labeling texts in a supervised manner in both existing datasets `DigiMag` and `Persian News`.


### DigiMag

A total of 8,515 articles scraped from [Digikala Online Magazine](https://www.digikala.com/mag/). This dataset includes seven different classes.

1. Video Games
2. Shopping Guide
3. Health Beauty
4. Science Technology
5. General
6. Art Cinema
7. Books Literature


|        Label       |   #  |
|:------------------:|:----:|
|     Video Games    | 1967 |
|   Shopping Guide   |  125 |
|    Health Beauty   | 1610 |
| Science Technology | 2772 |
|       General      |  120 |
|     Art Cinema     | 1667 |
|  Books Literature  |  254 |


**Download**
You can download the dataset from [here](https://drive.google.com/uc?id=1YgrCYY-Z0h2z0-PfWVfOGt1Tv0JDI-qz)


## Results

The following table summarizes the F1 score obtained by ParsBERT as compared to other models and architectures.

|      Dataset      | ALBERT-fa-base-v2 | ParsBERT-v1 | mBERT |
|:-----------------:|:-----------------:|:-----------:|:-----:|
| Digikala Magazine |       92.33       |    93.59    | 90.72 |



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