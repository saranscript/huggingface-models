---
language: pt
license: apache-2.0

widget:
- text: "O futuro de DI caiu 20 bps nesta manhã"
  example_title: "Example 1"
- text: "O Nubank decidiu cortar a faixa de preço da oferta pública inicial (IPO) após revés no humor dos mercados internacionais com as fintechs."
  example_title: "Example 2"
- text: "O Ibovespa acompanha correção do mercado e fecha com alta moderada"
  example_title: "Example 3"
---

# FinBertPTBR : Financial Bert PT BR

FinBertPTBR is a pre-trained NLP model to analyze sentiment of Brazilian Portuguese financial texts. It is built by further training the BERTimbau language model in the finance domain, using a large financial corpus and thereby fine-tuning it for financial sentiment classification.

## Usage
```python
from transformers import AutoTokenizer, AutoModel
  
tokenizer = AutoTokenizer.from_pretrained("turing-usp/FinBertPTBR")
model = AutoModel.from_pretrained("turing-usp/FinBertPTBR")
```

## Authors

  - [Vinicius Carmo](https://www.linkedin.com/in/vinicius-cleves/)
  - [Julia Pocciotti](https://www.linkedin.com/in/juliapocciotti/)
  - [Luísa Heise](https://www.linkedin.com/in/lu%C3%ADsa-mendes-heise/)
  - [Lucas Leme](https://www.linkedin.com/in/lucas-leme-santos/)
  