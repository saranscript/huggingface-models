# roberta-python
---
language: python
datasets:
- code_search_net
---

This is a [roberta](https://arxiv.org/pdf/1907.11692.pdf) pre-trained version on the [CodeSearchNet dataset](https://github.com/github/CodeSearchNet) for **Python** Mask Language Model mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead, pipeline
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/roberta-python")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/roberta-python")

fill_mask = pipeline(
    "fill-mask",
    model=model,
    tokenizer=tokenizer
)
```

You can then use this model to fill masked words in a Python code.

```python
code = """
new_dict = {}
for k, v in my_dict.<mask>():
    new_dict[k] = v**2
""".lstrip()

pred = {x["token_str"].replace("Ġ", ""): x["score"] for x in fill_mask(code)}
sorted(pred.items(), key=lambda kv: kv[1], reverse=True)
# [('items', 0.7376779913902283),
# ('keys', 0.16238391399383545),
# ('values', 0.03965481370687485),
# ('iteritems', 0.03346433863043785),
# ('splitlines', 0.0032723243348300457)]
```

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/CodeMLM)

> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)
