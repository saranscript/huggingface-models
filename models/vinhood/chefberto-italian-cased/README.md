---
language: it
license: mit
widget:
- text: "La pasta più semplice è aglio, [MASK] e peperoncino."
- text: "Per fare la carbonara servono le [MASK]." 
- text: "A tavola non può mancare del buon [MASK]."
---

# ChefBERTo 👨‍🍳 

**chefberto-italian-cased** is a BERT model obtained by MLM adaptive-tuning [**bert-base-italian-xxl-cased**](https://huggingface.co/dbmdz/bert-base-italian-xxl-cased) on Italian cooking recipes, approximately 50k sentences (2.6M words).

**Author:** Cristiano De Nobili ([@denocris](https://twitter.com/denocris) on Twitter, [LinkedIn](https://www.linkedin.com/in/cristiano-de-nobili/)) for [VINHOOD](https://www.vinhood.com/en/).
<p>
    <img src="https://drive.google.com/uc?export=view&id=1u5aY2wKu-X5DAzbOq7rsgGFW5_lGUAQn" width="400"> </br>
</p>

# Perplexity 

Test set: 9k sentences about food.

| Model | Perplexity | 
| ------ | ------ | 
| chefberto-italian-cased | **1.84**  | 
| bert-base-italian-xxl-cased | 2.85  |

# Usage

```python
from transformers import AutoModel, AutoTokenizer
model_name = "vinhood/chefberto-italian-cased"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
```