---
language: it
license: mit
widget:
- text: "Con del pesce bisogna bere un bicchiere di vino [MASK]."
- text: "Con la carne c'è bisogno del vino [MASK]."
- text: "A tavola non può mancare del buon [MASK]."
---

# WineBERTo 🍷🥂

**wineberto-italian-cased** is a BERT model obtained by MLM adaptive-tuning [**bert-base-italian-xxl-cased**](https://huggingface.co/dbmdz/bert-base-italian-xxl-cased) on Italian drink recipes and wine descriptions, approximately 77k sentences (3.3M words).

**Author:** Cristiano De Nobili ([@denocris](https://twitter.com/denocris) on Twitter, [LinkedIn](https://www.linkedin.com/in/cristiano-de-nobili/)) for [VINHOOD](https://www.vinhood.com/en/).
<p>
    <img src="https://drive.google.com/uc?export=view&id=1dco9I9uzevP2V6oku1salIYcovUAeqWE" width="400"> </br>
</p>

# Perplexity 

Test set: 14k sentences about wine.

| Model | Perplexity | 
| ------ | ------ | 
| wineberto-italian-cased | **2.29**  | 
| bert-base-italian-xxl-cased | 4.60  | 

# Usage

```python
from transformers import AutoModel, AutoTokenizer
model_name = "vinhood/wineberto-italian-cased"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
```