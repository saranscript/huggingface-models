---
language: jv
tags:
- javanese-distilbert-small-imdb-classifier
license: mit
datasets:
- w11wo/imdb-javanese
widget:
- text: "Aku babar pisan ora nikmati film iki."
---

## Javanese DistilBERT Small IMDB Classifier
Javanese DistilBERT Small IMDB Classifier is a movie-classification model based on the [DistilBERT model](https://arxiv.org/abs/1910.01108). It was trained on Javanese IMDB movie reviews.

The model was originally [`w11wo/javanese-distilbert-small-imdb`](https://huggingface.co/w11wo/javanese-distilbert-small-imdb) which is then fine-tuned on the [`w11wo/imdb-javanese`](https://huggingface.co/datasets/w11wo/imdb-javanese) dataset consisting of Javanese IMDB movie reviews. It achieved an accuracy of 76.04% on the validation dataset. Many of the techniques used are based on a Hugging Face tutorial [notebook](https://github.com/huggingface/notebooks/blob/master/examples/text_classification.ipynb) written by [Sylvain Gugger](https://github.com/sgugger).

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with TensorFlow nonetheless.

## Model
| Model                                       | #params | Arch.            | Training/Validation data (text) |
|---------------------------------------------|---------|------------------|---------------------------------|
| `javanese-distilbert-small-imdb-classifier` |   66M   | DistilBERT Small | Javanese IMDB (47.5 MB of text) |

## Evaluation Results
The model was trained for 5 epochs and the following is the final result once the training ended.

| train loss | valid loss |  accuracy  | total time |
|------------|------------|------------|------------|
|    0.131   |    1.113   |   0.760    |   1:26:4   |

## How to Use
### As Text Classifier
```python
from transformers import pipeline

pretrained_name = "w11wo/javanese-distilbert-small-imdb-classifier"

nlp = pipeline(
    "sentiment-analysis",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("Film sing apik banget!")
```

## Disclaimer
Do consider the biases which came from the IMDB review that may be carried over into the results of this model.

## Author
Javanese DistilBERT Small IMDB Classifier was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.

## Citation

If you use any of our models in your research, please cite:

```bib
@inproceedings{wongso2021causal,
    title={Causal and Masked Language Modeling of Javanese Language using Transformer-based Architectures},
    author={Wongso, Wilson and Setiawan, David Samuel and Suhartono, Derwin},
    booktitle={2021 International Conference on Advanced Computer Science and Information Systems (ICACSIS)},
    pages={1--7},
    year={2021},
    organization={IEEE}
}
```
