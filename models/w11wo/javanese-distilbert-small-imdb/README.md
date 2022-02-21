---
language: jv
tags:
- javanese-distilbert-small-imdb
license: mit
datasets:
- w11wo/imdb-javanese
widget:
- text: "Film favoritku yaiku Interstellar [MASK] Christopher Nolan."
---

## Javanese DistilBERT Small IMDB
Javanese DistilBERT Small IMDB is a masked language model based on the [DistilBERT model](https://arxiv.org/abs/1910.01108). It was trained on Javanese IMDB movie reviews.

The model was originally the pretrained [Javanese DistilBERT Small model](https://huggingface.co/w11wo/javanese-distilbert-small) and is later fine-tuned on the Javanese IMDB movie review dataset. It achieved a perplexity of 21.01 on the validation dataset. Many of the techniques used are based on a Hugging Face tutorial [notebook](https://github.com/huggingface/notebooks/blob/master/examples/language_modeling.ipynb) written by [Sylvain Gugger](https://github.com/sgugger).

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with TensorFlow nonetheless.

## Model
| Model                            | #params  | Arch.                | Training/Validation data (text) |
|----------------------------------|----------|----------------------|---------------------------------|
| `javanese-distilbert-small-imdb` |   66M    |   DistilBERT Small   | Javanese IMDB (47.5 MB of text) |

## Evaluation Results
The model was trained for 5 epochs and the following is the final result once the training ended.

| train loss | valid loss | perplexity | total time  |
|------------|------------|------------|-------------|
|    3.126   |    3.039   |   21.01    |    5:6:4    |

## How to Use
### As Masked Language Model
```python
from transformers import pipeline

pretrained_name = "w11wo/javanese-distilbert-small-imdb"

fill_mask = pipeline(
    "fill-mask",
    model=pretrained_name,
    tokenizer=pretrained_name
)

fill_mask("Aku mangan sate ing [MASK] bareng konco-konco")
```
### Feature Extraction in PyTorch
```python
from transformers import DistilBertModel, DistilBertTokenizerFast

pretrained_name = "w11wo/javanese-distilbert-small-imdb"
model = DistilBertModel.from_pretrained(pretrained_name)
tokenizer = DistilBertTokenizerFast.from_pretrained(pretrained_name)

prompt = "Indonesia minangka negara gedhe."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer
Do consider the biases which came from the IMDB review that may be carried over into the results of this model.

## Author
Javanese DistilBERT Small was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.

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
