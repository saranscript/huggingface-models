---
language: ms
tags:
- malaysian-distilbert-small
license: mit
datasets:
- oscar
widget:
- text: "Hari ini adalah hari yang [MASK]!"
---

## Malaysian DistilBERT Small
Malaysian DistilBERT Small is a masked language model based on the [DistilBERT model](https://arxiv.org/abs/1910.01108). It was trained on the [OSCAR](https://huggingface.co/datasets/oscar) dataset, specifically the `unshuffled_original_ms` subset.

The model was originally HuggingFace's pretrained [English DistilBERT model](https://huggingface.co/distilbert-base-uncased) and is later fine-tuned on the Malaysian dataset. It achieved a perplexity of 10.33 on the validation dataset (20% of the dataset). Many of the techniques used are based on a Hugging Face tutorial [notebook](https://github.com/huggingface/notebooks/blob/master/examples/language_modeling.ipynb) written by [Sylvain Gugger](https://github.com/sgugger), and [fine-tuning tutorial notebook](https://github.com/piegu/fastai-projects/blob/master/finetuning-English-GPT2-any-language-Portuguese-HuggingFace-fastaiv2.ipynb) written by [Pierre Guillou](https://huggingface.co/pierreguillou).

Hugging Face's [Transformers](https://huggingface.co/transformers) library was used to train the model -- utilizing the base DistilBERT model and their `Trainer` class. PyTorch was used as the backend framework during training, but the model remains compatible with TensorFlow nonetheless.

## Model
| Model                        | #params | Arch.            | Training/Validation data (text)        |
|------------------------------|---------|------------------|----------------------------------------|
| `malaysian-distilbert-small` |   66M   | DistilBERT Small | OSCAR `unshuffled_original_ms` Dataset |

## Evaluation Results
The model was trained for 1 epoch and the following is the final result once the training ended.

| train loss | valid loss | perplexity | total time |
|------------|------------|------------|------------|
|    2.476   |    2.336   |   10.33    |   0:40:05  |

## How to Use
### As Masked Language Model
```python
from transformers import pipeline

pretrained_name = "w11wo/malaysian-distilbert-small"

fill_mask = pipeline(
    "fill-mask",
    model=pretrained_name,
    tokenizer=pretrained_name
)

fill_mask("Henry adalah seorang lelaki yang tinggal di [MASK].")
```
### Feature Extraction in PyTorch
```python
from transformers import DistilBertModel, DistilBertTokenizerFast

pretrained_name = "w11wo/malaysian-distilbert-small"
model = DistilBertModel.from_pretrained(pretrained_name)
tokenizer = DistilBertTokenizerFast.from_pretrained(pretrained_name)

prompt = "Bolehkah anda [MASK] Bahasa Melayu?"
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer
Do consider the biases which came from the OSCAR dataset that may be carried over into the results of this model.

## Author
Malaysian DistilBERT Small was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.