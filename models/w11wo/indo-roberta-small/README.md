---
language: id
tags:
- indo-roberta-small
license: mit
datasets:
- wikipedia
widget:
- text: "Karena pandemi ini, kita harus <mask> di rumah saja."
---

## Indo RoBERTa Small
Indo RoBERTa Small is a masked language model based on the [RoBERTa model](https://arxiv.org/abs/1907.11692). It was trained on the latest (late December 2020) Indonesian Wikipedia articles.

The model was trained from scratch and achieved a perplexity of 48.27 on the validation dataset (20% of the articles). Many of the techniques used
are based on a Hugging Face tutorial [notebook](https://github.com/huggingface/notebooks/blob/master/examples/language_modeling.ipynb) written by [Sylvain Gugger](https://github.com/sgugger), where Sylvain Gugger fine-tuned a [DistilGPT-2](https://huggingface.co/distilgpt2) on [Wikitext2](https://render.githubusercontent.com/view/ipynb?color_mode=dark&commit=43d63e390e8a82f7ae49aa1a877419343a213cb4&enc_url=68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f68756767696e67666163652f6e6f7465626f6f6b732f343364363365333930653861383266376165343961613161383737343139333433613231336362342f6578616d706c65732f6c616e67756167655f6d6f64656c696e672e6970796e62&nwo=huggingface%2Fnotebooks&path=examples%2Flanguage_modeling.ipynb&repository_id=272452525&repository_type=Repository).

Hugging Face's [Transformers]((https://huggingface.co/transformers)) library was used to train the model -- utilizing the base RoBERTa model and their `Trainer` class. PyTorch was used as the backend framework during training, but the model remains compatible with TensorFlow nonetheless.

## Model
| Model                | #params | Arch.    | Training/Validation data (text)      |
|----------------------|---------|----------|---------------------------------------|
| `indo-roberta-small` |   84M   | RoBERTa  | Indonesian Wikipedia (3.1 GB of text) |

## Evaluation Results
The model was trained for 3 epochs and the following is the final result once the training ended.

| train loss | valid loss | perplexity | total time |
|------------|------------|------------|------------|
|    4.071   |    3.876   |    48.27   |   3:40:55  |

## How to Use
### As Masked Language Model
```python
from transformers import pipeline

pretrained_name = "w11wo/indo-roberta-small"

fill_mask = pipeline(
    "fill-mask",
    model=pretrained_name,
    tokenizer=pretrained_name
)

fill_mask("Budi sedang <mask> di sekolah.")
```
### Feature Extraction in PyTorch
```python
from transformers import RobertaModel, RobertaTokenizerFast

pretrained_name = "w11wo/indo-roberta-small"
model = RobertaModel.from_pretrained(pretrained_name)
tokenizer = RobertaTokenizerFast.from_pretrained(pretrained_name)

prompt = "Budi sedang berada di sekolah."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer
Do remember that although the dataset originated from Wikipedia, the model may not always generate factual texts. Additionally, the biases which came from the Wikipedia articles may be carried over into the results of this model.

## Author
Indo RoBERTa Small was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.