# t5_wikisql_SQL2en
---
language: en
datasets:
- wikisql
---

This is a [t5-small](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) fine-tuned version on the [wikisql dataset](https://huggingface.co/datasets/wikisql) for **SQL** to **English** **translation** text2text mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/t5_wikisql_SQL2en")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/t5_wikisql_SQL2en")
```

You can then use this model to translate SQL queries into plain english.

```python
query = "SELECT people FROM peoples where age > 10"
input_text = f"translate SQL to English: {query} </s>"
features = tokenizer([input_text], return_tensors='pt')

output = model.generate(input_ids=features['input_ids'].cuda(), 
                        attention_mask=features['attention_mask'].cuda())

tokenizer.decode(output[0])
# Output: "What people are older than 10?"
```

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/SQLM)

> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)
