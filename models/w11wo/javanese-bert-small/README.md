---
language: jv
tags:
- javanese-bert-small
license: mit
datasets:
- wikipedia
widget:
- text: "Aku mangan sate ing [MASK] bareng konco-konco"
---

## Javanese BERT Small
Javanese BERT Small is a masked language model based on the [BERT model](https://arxiv.org/abs/1810.04805). It was trained on the latest (late December 2020) Javanese Wikipedia articles.

The model was originally HuggingFace's pretrained [English BERT model](https://huggingface.co/bert-base-uncased) and is later fine-tuned on the Javanese dataset. It achieved a perplexity of 22.00 on the validation dataset (20% of the articles). Many of the techniques used are based on a Hugging Face tutorial [notebook](https://github.com/huggingface/notebooks/blob/master/examples/language_modeling.ipynb) written by [Sylvain Gugger](https://github.com/sgugger), and [fine-tuning tutorial notebook](https://github.com/piegu/fastai-projects/blob/master/finetuning-English-GPT2-any-language-Portuguese-HuggingFace-fastaiv2.ipynb) written by [Pierre Guillou](https://huggingface.co/pierreguillou).

Hugging Face's [Transformers](https://huggingface.co/transformers) library was used to train the model -- utilizing the base BERT model and their `Trainer` class. PyTorch was used as the backend framework during training, but the model remains compatible with TensorFlow nonetheless.

## Model
| Model                 | #params  | Arch.          | Training/Validation data (text)     |
|-----------------------|----------|----------------|-------------------------------------|
| `javanese-bert-small` |   110M   |   BERT Small   | Javanese Wikipedia (319 MB of text) |

## Evaluation Results
The model was trained for 5 epochs and the following is the final result once the training ended.

| train loss | valid loss | perplexity | total time |
|------------|------------|------------|------------|
|    3.116   |    3.091   |   22.00    |   2:7:42   |

## How to Use
### As Masked Language Model
```python
from transformers import pipeline

pretrained_name = "w11wo/javanese-bert-small"

fill_mask = pipeline(
    "fill-mask",
    model=pretrained_name,
    tokenizer=pretrained_name
)

fill_mask("Aku mangan sate ing [MASK] bareng konco-konco")
```
### Feature Extraction in PyTorch
```python
from transformers import BertModel, BertTokenizerFast

pretrained_name = "w11wo/javanese-bert-small"
model = BertModel.from_pretrained(pretrained_name)
tokenizer = BertTokenizerFast.from_pretrained(pretrained_name)

prompt = "Indonesia minangka negara gedhe."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer
Do remember that although the dataset originated from Wikipedia, the model may not always generate factual texts. Additionally, the biases which came from the Wikipedia articles may be carried over into the results of this model.

## Author
Javanese BERT Small was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.

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
