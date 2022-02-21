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


### Persian News

A dataset of various news articles scraped from different online news agencies' websites. The total number of articles is 16,438, spread over eight different classes.

1. Economic
2. International
3. Political
4. Science Technology
5. Cultural Art
6. Sport
7. Medical


|        Label       |   #  |
|:------------------:|:----:|
|       Social       | 2170 |
|      Economic      | 1564 |
|    International   | 1975 |
|      Political     | 2269 |
| Science Technology | 2436 |
|    Cultural Art    | 2558 |
|        Sport       | 1381 |
|       Medical      | 2085 |


**Download**
You can download the dataset from [here](https://drive.google.com/uc?id=1B6xotfXCcW9xS1mYSBQos7OCg0ratzKC)


## Results

The following table summarizes the F1 score obtained as compared to other models and architectures.

|      Dataset      | ALBERT-fa-base-v2 | ParsBERT-v1 | mBERT |
|:-----------------:|:-----------------:|:-----------:|:-----:|
|    Persian News   |       97.01       |    97.19    | 95.79 |



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