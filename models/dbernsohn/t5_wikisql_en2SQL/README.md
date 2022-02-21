# t5_wikisql_en2SQL
---
language: en
datasets:
- wikisql
---

This is a [t5-small](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) fine-tuned version on the [wikisql dataset](https://huggingface.co/datasets/wikisql) for **English** to **SQL** **translation** text2text mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/t5_wikisql_en2SQL")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/t5_wikisql_en2SQL")
```

You can then use this model to translate SQL queries into plain english.

```python
query = "what are the names of all the people in the USA?"
input_text = f"translate English to Sql: {query} </s>"
features = tokenizer([input_text], return_tensors='pt')

output = model.generate(input_ids=features['input_ids'].cuda(), 
                        attention_mask=features['attention_mask'].cuda())

tokenizer.decode(output[0])
# Output: "SELECT Name FROM table WHERE Country = USA"
```

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/SQLM)

> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)