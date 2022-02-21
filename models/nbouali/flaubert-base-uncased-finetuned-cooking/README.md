---
language: fr
tags: 
- text-classification
- flaubert 
- french
- flaubert-base-uncased
widget:
- text: "Lasagnes à la bolognaise"
---
# FlauBERT finetuned on French cooking recipes


This model is finetuned on a sequence classification task that associates each sequence with the appropriate recipe category.

### How to use it?

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
from transformers import TextClassificationPipeline

loaded_tokenizer = AutoTokenizer.from_pretrained("nbouali/flaubert-base-uncased-finetuned-cooking")
loaded_model = AutoModelForSequenceClassification.from_pretrained("nbouali/flaubert-base-uncased-finetuned-cooking")

nlp = TextClassificationPipeline(model=loaded_model,tokenizer=loaded_tokenizer,task="Recipe classification")

print(nlp("Lasagnes à la bolognaise"))
```

```
[{'label': 'LABEL_6', 'score': 0.9921900033950806}]
```
### Label encoding:

| label | Recipe Category |
|:------:|:--------------:|
|     0 |'Accompagnement' |
|     1 |  'Amuse-gueule' |
|     2 | 'Boisson' |
|     3 | 'Confiserie' |
|     4 | 'Dessert'|
|     5 | 'Entrée' |
|     6 |'Plat principal' |
|     7 | 'Sauce' |


<br/>
<br/>

> If you would like to know more about this model you can refer to [our blog post](https://medium.com/unify-data-office/a-cooking-language-model-fine-tuned-on-dozens-of-thousands-of-french-recipes-bcdb8e560571)