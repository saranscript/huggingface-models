---
language: pt
tags:
- question-answering
- bert
- bioBERTpt
- pytorch
metrics:
- squad
widget:
- text: "O que é AVC?"
  context: "O AVC (Acidente vascular cerebral) é a segunda principal causa de morte no Brasil e a principal causa de incapacidade em adultos, retirando do mercado de trabalho milhares de brasileiros. A cada 5 minutos ocorre uma morte por AVC em nosso país. Ele é uma alteração súbita na circulação de sangue em alguma região encéfalo (composto pelo cérebro, cerebelo e tronco encefálico)."
- text: "O que significa a sigla AVC?"
  context: "O AVC (Acidente vascular cerebral) é a segunda principal causa de morte no Brasil e a principal causa de incapacidade em adultos, retirando do mercado de trabalho milhares de brasileiros. A cada 5 minutos ocorre uma morte por AVC em nosso país. Ele é uma alteração súbita na circulação de sangue em alguma região encéfalo (composto pelo cérebro, cerebelo e tronco encefálico)."
- text: "Do que a região do encéfalo é composta?"
  context: "O AVC (Acidente vascular cerebral) é a segunda principal causa de morte no Brasil e a principal causa de incapacidade em adultos, retirando do mercado de trabalho milhares de brasileiros. A cada 5 minutos ocorre uma morte por AVC em nosso país. Ele é uma alteração súbita na circulação de sangue em alguma região encéfalo (composto pelo cérebro, cerebelo e tronco encefálico)."
- text: "O que causa a interrupção do oxigênio?"
  context: "O oxigênio é um elemento essencial para a atividade normal do nosso corpo; ele juntamente com os nutrientes são transportados pelo sangue, através das nossas artérias, estas funcionam como mangueiras direcionando o sangue para regiões específicas. Quando esse transporte é impedido e o oxigênio não chega as áreas necessárias parte do encéfalo não consegue obter o sangue (e oxigênio) de que precisa, então ele e as células sofrem lesão ou morrem. Essa interrupção pode ser causada por duas razões, um entupimento ou um vazamento nas artérias. desta forma temos dois tipos de AVC." 
---
# BioBERTpt-squad-v1.1-portuguese for QA (Question Answering)

This is a clinical and biomedical model trained with generic QA questions. This model was finetuned on SQUAD v1.1, with the dataset SQUAD v1.1 in portuguese, from the Deep Learning Brasil group on Google Colab. See more details [here](https://huggingface.co/pierreguillou/bert-base-cased-squad-v1.1-portuguese).

## Performance
The results obtained are the following:
```
f1 = 80.06
exact match = 67.52
```
## See more
Our repo: https://github.com/HAILab-PUCPR/