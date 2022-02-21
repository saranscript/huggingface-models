---
language: jv
tags:
- javanese-gpt2-small-imdb
license: mit
datasets:
- w11wo/imdb-javanese
widget:
- text: "Train to Busan yaiku film sing digawe ing Korea Selatan"
---

## Javanese GPT-2 Small IMDB
Javanese GPT-2 Small IMDB is a causal language model based on the [GPT-2 model](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf). It was trained on Javanese IMDB movie reviews.

The model was originally the pretrained [Javanese GPT-2 Small model](https://huggingface.co/w11wo/javanese-gpt2-small) and is later fine-tuned on the Javanese IMDB movie review dataset. It achieved a perplexity of 60.54 on the validation dataset. Many of the techniques used are based on a Hugging Face tutorial [notebook](https://github.com/huggingface/notebooks/blob/master/examples/language_modeling.ipynb) written by [Sylvain Gugger](https://github.com/sgugger).

Hugging Face's `Trainer` class from the [Transformers]((https://huggingface.co/transformers)) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with TensorFlow nonetheless.

## Model
| Model                      | #params  | Arch.           | Training/Validation data (text) |
|----------------------------|----------|-----------------|---------------------------------|
| `javanese-gpt2-small-imdb` |   124M   |   GPT-2 Small   | Javanese IMDB (47.5 MB of text) |

## Evaluation Results
The model was trained for 5 epochs and the following is the final result once the training ended.

| train loss | valid loss | perplexity | total time |
|------------|------------|------------|------------|
|    4.135   |    4.103   |   60.54    |   6:22:40  |

## How to Use (PyTorch)
### As Causal Language Model
```python
from transformers import pipeline

pretrained_name = "w11wo/javanese-gpt2-small-imdb"

nlp = pipeline(
    "text-generation",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("Jenengku Budi, saka Indonesia")
```
### Feature Extraction in PyTorch
```python
from transformers import GPT2LMHeadModel, GPT2TokenizerFast

pretrained_name = "w11wo/javanese-gpt2-small-imdb"
model = GPT2LMHeadModel.from_pretrained(pretrained_name)
tokenizer = GPT2TokenizerFast.from_pretrained(pretrained_name)

prompt = "Indonesia minangka negara gedhe."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer
Do consider the biases which came from the IMDB review that may be carried over into the results of this model.

## Author
Javanese GPT-2 Small was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.

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
