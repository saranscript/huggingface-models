# roberta-java
---
language: Java
datasets:
- code_search_net
---

This is a [roberta](https://arxiv.org/pdf/1907.11692.pdf) pre-trained version on the [CodeSearchNet dataset](https://github.com/github/CodeSearchNet) for **Java** Mask Language Model mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead, pipeline
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/roberta-java")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/roberta-java")

fill_mask = pipeline(
    "fill-mask",
    model=model,
    tokenizer=tokenizer
)
```

You can then use this model to fill masked words in a Java code.

```python
code = """
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
for (String i : cars) {
System.out.<mask>(i);
}
""".lstrip()

pred = {x["token_str"].replace("Ġ", ""): x["score"] for x in fill_mask(code)}
sorted(pred.items(), key=lambda kv: kv[1], reverse=True)
# [('println', 0.32571351528167725),
# ('get', 0.2897663116455078),
# ('remove', 0.0637081190943718),
# ('exit', 0.058875661343336105),
# ('print', 0.034190207719802856)]
```

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/CodeMLM)

> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)