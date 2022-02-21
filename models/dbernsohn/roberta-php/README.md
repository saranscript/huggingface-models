# roberta-php
---
language: php
datasets:
- code_search_net
---

This is a [roberta](https://arxiv.org/pdf/1907.11692.pdf) pre-trained version on the [CodeSearchNet dataset](https://github.com/github/CodeSearchNet) for **php** Mask Language Model mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead, pipeline
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/roberta-php")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/roberta-php")

fill_mask = pipeline(
    "fill-mask",
    model=model,
    tokenizer=tokenizer
)
```

You can then use this model to fill masked words in a Java code.

```python
code = """
$people = array(
    array('name' => 'Kalle', 'salt' => 856412),
    array('name' => 'Pierre', 'salt' => 215863)
);

for($i = 0; $i < count($<mask>); ++$i) {
    $people[$i]['salt'] = mt_rand(000000, 999999);
}
""".lstrip()

pred = {x["token_str"].replace("Ġ", ""): x["score"] for x in fill_mask(code)}
sorted(pred.items(), key=lambda kv: kv[1], reverse=True)
# [('people', 0.785636842250824),
#  ('parts', 0.006270722020417452),
#  ('id', 0.0035842324141412973),
#  ('data', 0.0025512021966278553),
#  ('config', 0.002258970635011792)]
```

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/CodeMLM)

> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)