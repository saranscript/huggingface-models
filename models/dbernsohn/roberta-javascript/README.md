# roberta-javascript
---
language: javascript
datasets:
- code_search_net
---

This is a [roberta](https://arxiv.org/pdf/1907.11692.pdf) pre-trained version on the [CodeSearchNet dataset](https://github.com/github/CodeSearchNet) for **javascript** Mask Language Model mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead, pipeline
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/roberta-javascript")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/roberta-javascript")

fill_mask = pipeline(
    "fill-mask",
    model=model,
    tokenizer=tokenizer
)
```

You can then use this model to fill masked words in a Java code.

```python
code = """
var i;
for (i = 0; i < cars.<mask>; i++) {
  text += cars[i] + "<br>";
}
""".lstrip()

pred = {x["token_str"].replace("Ġ", ""): x["score"] for x in fill_mask(code)}
sorted(pred.items(), key=lambda kv: kv[1], reverse=True)
# [('length', 0.9959614872932434),
#  ('i', 0.00027875584783032537),
#  ('len', 0.0002283261710545048),
#  ('nodeType', 0.00013731322542298585),
#  ('index', 7.5289819505997e-05)]
```

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/CodeMLM)

> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)