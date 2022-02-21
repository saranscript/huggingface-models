---
language: 
- pt-br
tags:
- question-answering
license: apache-2.0
pipeline_tag: question-answering
metrics:
- em
- f1
---

# BraQuAD BERT

## Model description

This is a question-answering model trained in BraQuAD 2.0, a version of SQuAD 2.0 translated to PT-BR using Google Cloud Translation API.

### Context
Edith Ranzini (São Paulo,[1] 1946) é uma engenheira brasileira formada pela USP, professora doutora da Pontifícia Universidade Católica de São Paulo[2] e professora sênior da Escola Politécnica da Universidade de São Paulo (Poli).[3] Ela compôs a equipe responsável pela  criação do primeiro computador brasileiro, o Patinho Feio,[1] em 1972, e participou do grupo de instituidores  da Fundação para o Desenvolvimento Tecnológico da Engenharia, sendo a única mulher do mesmo.[4][2] Atua nas áreas de inteligência artificial, engenharia de computação, redes neurais e sistemas gráficos.

Na sua época de prestar o vestibular, inscreveu-se para física na USP e para engenharia na Poli-USP,[3] sendo aprovada nesta última em 1965, ingressando como uma das 12 mulheres do total de 360 calouros.

Em 1969, formou-se como engenheira de eletricidade, permanecendo na universidade para fazer sua pós-graduação. Nessa época entrou para o Laboratório de Sistemas Digitais (LSD),atual Departamento de Engenharia de Computação e Sistemas Digitais, criado pelo professor Antônio Hélio Guerra Vieira.[3] Em 1970, deu início ao seu mestrado em Engenharia de Sistemas pela USP, concluindo o mesmo em 1975.[2] Nesse período, permaneceu no LSD e  fez parte do grupo responsável pelo desenvolvimento do primeiro computador brasileiro, o Patinho Feio (1971-1972) e do  G10 (1973-1975), primeiro computador brasileiro de médio porte,  feito para o Grupo de trabalho Especial (GTE), posteriormente Digibras.


### Examples:
 
1-Alem do Patinho feio qual outro projeto edith trabalhou? Answer: G10

2-Quantas mulheres entraram na Poli em 1965? Answer: 12

3-Qual grande projeto edith trabalhou? Answer: do primeiro computador brasileiro

4-Qual o primeiro computador brasileiro? Answer: Patinho Feio

## Expected results

As for an example, let's show a context and some questions you can ask, as well as the expected responses. This QnA pairs were not part of the training dataset.



#### How to use

```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer
import torch

mname = "piEsposito/braquad-bert-qna"
model = AutoModelForQuestionAnswering.from_pretrained(mname)
tokenizer = AutoTokenizer.from_pretrained(mname)

context = """Edith Ranzini (São Paulo,[1] 1946) é uma engenheira brasileira formada pela USP, professora doutora da Pontifícia Universidade Católica de São Paulo[2] e professora sênior da Escola Politécnica da Universidade de São Paulo (Poli).[3] Ela compôs a equipe responsável pela  criação do primeiro computador brasileiro, o Patinho Feio,[1] em 1972, e participou do grupo de instituidores  da Fundação para o Desenvolvimento Tecnológico da Engenharia, sendo a única mulher do mesmo.[4][2] Atua nas áreas de inteligência artificial, engenharia de computação, redes neurais e sistemas gráficos.

Na sua época de prestar o vestibular, inscreveu-se para física na USP e para engenharia na Poli-USP,[3] sendo aprovada nesta última em 1965, ingressando como uma das 12 mulheres do total de 360 calouros.[5]

Em 1969, formou-se como engenheira de eletricidade,[2][3] permanecendo na universidade para fazer sua pós-graduação. Nessa época entrou para o Laboratório de Sistemas Digitais (LSD),atual Departamento de Engenharia de Computação e Sistemas Digitais, criado pelo professor Antônio Hélio Guerra Vieira.[3] Em 1970, deu início ao seu mestrado em Engenharia de Sistemas pela USP, concluindo o mesmo em 1975.[2] Nesse período, permaneceu no LSD e  fez parte do grupo responsável pelo desenvolvimento do primeiro computador brasileiro, o Patinho Feio (1971-1972) e do  G10 (1973-1975), primeiro computador brasileiro de médio porte,  feito para o Grupo de trabalho Especial (GTE), posteriormente Digibras."""
# you can try this for all the examples above.

question = 'Qual grande projeto edith trabalhou?'

string = f"[CLS] {question} [SEP] {context} [SEP]"

as_tensor = torch.Tensor(tokenizer.encode(string)).unsqueeze(0)
starts, ends = model(as_tensor.long())
s, e = torch.argmax(starts[0]), torch.argmax(ends[0])

print(tokenizer.decode(tokenizer.encode(string)[s:e+1])) # 'do primeiro computador brasileiro'
```

#### Limitations and bias

- The model is trained on a dataset translated using Google Cloud API. Due to that, there are some issues with the labels, in some cases, not being identic to the answers. Due to that, the performance cannot reach the level it does with english, handly curated models. Anyway, it is a good progresso towards QnA in PT-BR.


## Training data

[BraQuAD dataset](https://github.com/piEsposito/br-quad-2.0).


## Training procedure


## Eval results

EM   | F1 
-------|---------
0.62  | 0.69


### BibTeX entry and citation info

```bibtex
@inproceedings{...,
  year={2020},
  title={BraQuAD - Dataset para Question Answering em PT-BR},
  author={Esposito, Wladimir and Esposito, Piero and Tamais, Ana},
}
```
