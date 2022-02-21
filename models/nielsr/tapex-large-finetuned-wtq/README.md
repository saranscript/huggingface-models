---
language: en
tags:
- tapex
- table-question-answering
license: apache-2.0
datasets:
- wtq
inference: false
---

TAPEX-large model fine-tuned on WTQ. This model was proposed in [TAPEX: Table Pre-training via Learning a Neural SQL Executor](https://arxiv.org/abs/2107.07653) by Qian Liu, Bei Chen, Jiaqi Guo, Morteza Ziyadi, Zeqi Lin, Weizhu Chen, Jian-Guang Lou. Original repo can be found [here](https://github.com/microsoft/Table-Pretraining).

To load it and run inference, you can do the following:

```
from transformers import BartTokenizer, BartForConditionalGeneration
import pandas as pd

tokenizer = BartTokenizer.from_pretrained("nielsr/tapex-large-finetuned-wtq")
model = BartForConditionalGeneration.from_pretrained("nielsr/tapex-large-finetuned-wtq")

# create table
data = {'Actors': ["Brad Pitt", "Leonardo Di Caprio", "George Clooney"], 'Number of movies': ["87", "53", "69"]}
table = pd.DataFrame.from_dict(data)

# turn into dict
table_dict = {"header": list(table.columns), "rows": [list(row.values) for i,row in table.iterrows()]}

# turn into format TAPEX expects
# define the linearizer based on this code: https://github.com/microsoft/Table-Pretraining/blob/main/tapex/processor/table_linearize.py
linearizer = IndexedRowTableLinearize()
linear_table = linearizer.process_table(table_dict)

# add question
question = "how many movies does George Clooney have?"
joint_input = question + " " + linear_table

# encode 
encoding = tokenizer(joint_input, return_tensors="pt")

# forward pass
outputs = model.generate(**encoding)

# decode
tokenizer.batch_decode(outputs, skip_special_tokens=True)
```