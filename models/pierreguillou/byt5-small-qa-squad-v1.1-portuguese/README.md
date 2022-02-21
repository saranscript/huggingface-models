---
language: pt 
license: apache-2.0
tags:
- text2text-generation
- byt5
- pytorch
- qa
datasets: squad
metrics: squad
widget:
- text: 'question: "Quando começou a pandemia de Covid-19 no mundo?" context: "A pandemia de COVID-19, também conhecida como pandemia de coronavírus, é uma pandemia em curso de COVID-19, uma doença respiratória aguda causada pelo coronavírus da síndrome respiratória aguda grave 2 (SARS-CoV-2). A doença foi identificada pela primeira vez em Wuhan, na província de Hubei, República Popular da China, em 1 de dezembro de 2019, mas o primeiro caso foi reportado em 31 de dezembro do mesmo ano."'
- text: 'question: "Onde foi descoberta a Covid-19?" context: "A pandemia de COVID-19, também conhecida como pandemia de coronavírus, é uma pandemia em curso de COVID-19, uma doença respiratória aguda causada pelo coronavírus da síndrome respiratória aguda grave 2 (SARS-CoV-2). A doença foi identificada pela primeira vez em Wuhan, na província de Hubei, República Popular da China, em 1 de dezembro de 2019, mas o primeiro caso foi reportado em 31 de dezembro do mesmo ano."' 
---

# ByT5 small finetuned for Question Answering (QA) on SQUaD v1.1 Portuguese
![Exemple of what can do the Portuguese ByT5 small QA (Question Answering), finetuned on SQUAD v1.1](https://miro.medium.com/max/2000/1*te5MmdesAHCmg4KmK8zD3g.png)

Check our other QA models in Portuguese finetuned on SQUAD v1.1:
- [Portuguese BERT base cased QA](https://huggingface.co/pierreguillou/bert-base-cased-squad-v1.1-portuguese)
- [Portuguese BERT large cased QA](https://huggingface.co/pierreguillou/bert-large-cased-squad-v1.1-portuguese)
- [Portuguese T5 base QA](https://huggingface.co/pierreguillou/t5-base-qa-squad-v1.1-portuguese)

## Introduction

The model was trained on the dataset SQUAD v1.1 in portuguese from the [Deep Learning Brasil group](http://www.deeplearningbrasil.com.br/) on Google Colab from the language model [ByT5 small](https://huggingface.co/google/byt5-small) of Google.

## About ByT5

ByT5 is a tokenizer-free version of [Google's T5](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) and generally follows the architecture of [MT5](https://huggingface.co/google/mt5-small). ByT5 was only pre-trained on [mC4](https://www.tensorflow.org/datasets/catalog/c4#c4multilingual) excluding any supervised training with an average span-mask of 20 UTF-8 characters. Therefore, this model has to be fine-tuned before it is useable on a downstream task.

ByT5 works especially well on noisy text data,*e.g.*, `google/byt5-small` significantly outperforms [mt5-small](https://huggingface.co/google/mt5-small) on [TweetQA](https://arxiv.org/abs/1907.06292).

Paper: [ByT5: Towards a token-free future with pre-trained byte-to-byte models](https://arxiv.org/abs/2105.13626)

## Informations on the method used

All the informations are in the blog post : ...

## Notebooks in Google Colab & GitHub

- Google Colab: ...
- GitHub: ...

## Performance

The results obtained are the following:

```
f1 = ...
exact match = ...
```

## How to use the model... with Pipeline

```python
import transformers
from transformers import pipeline

model_name = 'pierreguillou/byt5-small-qa-squad-v1.1-portuguese'
nlp = pipeline("text2text-generation", model=model_name)

# source: https://pt.wikipedia.org/wiki/Pandemia_de_COVID-19
input_text = r"""
question: "Quando começou a pandemia de Covid-19 no mundo?" 
context: "A pandemia de COVID-19, também conhecida como pandemia de coronavírus, é uma pandemia em curso de COVID-19, uma doença respiratória aguda causada pelo coronavírus da síndrome respiratória aguda grave 2 (SARS-CoV-2). A doença foi identificada pela primeira vez em Wuhan, na província de Hubei, República Popular da China, em 1 de dezembro de 2019, mas o primeiro caso foi reportado em 31 de dezembro do mesmo ano."
"""
input_text = input_text.replace('\n','')
input_text

# question: "Quando começou a pandemia de Covid-19 no mundo?" context: "A pandemia de COVID-19, também conhecida como pandemia de coronavírus, é uma pandemia em curso de COVID-19, uma doença respiratória aguda causada pelo coronavírus da síndrome respiratória aguda grave 2 (SARS-CoV-2). A doença foi identificada pela primeira vez em Wuhan, na província de Hubei, República Popular da China, em 1 de dezembro de 2019, mas o primeiro caso foi reportado em 31 de dezembro do mesmo ano."

result = nlp(input_text)
result

# [{'generated_text': '1 de dezembro de 2019'}]
```

## How to use the model... with the Auto classes

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
 
model_name = 'pierreguillou/byt5-small-qa-squad-v1.1-portuguese'
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSeq2SeqLM.from_pretrained(model_name)

# source: https://pt.wikipedia.org/wiki/Pandemia_de_COVID-19
input_text = r"""
question: "Quando começou a pandemia de Covid-19 no mundo?" 
context: "A pandemia de COVID-19, também conhecida como pandemia de coronavírus, é uma pandemia em curso de COVID-19, uma doença respiratória aguda causada pelo coronavírus da síndrome respiratória aguda grave 2 (SARS-CoV-2). A doença foi identificada pela primeira vez em Wuhan, na província de Hubei, República Popular da China, em 1 de dezembro de 2019, mas o primeiro caso foi reportado em 31 de dezembro do mesmo ano."
"""
input_text = input_text.replace('\n','')
input_text

# question: "Quando começou a pandemia de Covid-19 no mundo?" context: "A pandemia de COVID-19, também conhecida como pandemia de coronavírus, é uma pandemia em curso de COVID-19, uma doença respiratória aguda causada pelo coronavírus da síndrome respiratória aguda grave 2 (SARS-CoV-2). A doença foi identificada pela primeira vez em Wuhan, na província de Hubei, República Popular da China, em 1 de dezembro de 2019, mas o primeiro caso foi reportado em 31 de dezembro do mesmo ano."

input_ids = tokenizer(input_text, return_tensors='pt').input_ids
outputs = model.generate(
    input_ids,
    max_length=64,
    num_beams=1
    )
    
result = tokenizer.decode(outputs[0], skip_special_tokens=True, clean_up_tokenization_spaces=True)
result

# 1 de dezembro de 2019
```             

## Limitations and bias

The training data used for this model come from Portuguese SQUAD. It could contain a lot of unfiltered content, which is far from neutral, and biases.

## Author

Portuguese ByT5 small QA (Question Answering), finetuned on SQUAD v1.1 was trained and evaluated by [Pierre GUILLOU](https://www.linkedin.com/in/pierreguillou/) thanks to the Open Source code, platforms and advices of many organizations. In particular: [Google AI](https://huggingface.co/google), [Hugging Face](https://huggingface.co/), [Deep Learning Brasil group](http://www.deeplearningbrasil.com.br/) and [Google Colab](https://colab.research.google.com/).

## Citation
If you use our work, please cite:

```bibtex
@inproceedings{pierreguillou2021byt5smallsquadv11portuguese,
  title={Portuguese ByT5 small QA (Question Answering), finetuned on SQUAD v1.1},
  author={Pierre Guillou},
  year={2021}
}
```