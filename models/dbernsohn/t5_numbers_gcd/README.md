# numbers_gcd
---
language: en
datasets:
- numbers_gcd
---

This is a [t5-small](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) fine-tuned version on the [math_dataset/numbers_gcd](https://www.tensorflow.org/datasets/catalog/math_dataset#mathdatasetnumbers_gcd) for solving **greatest common divisor** mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/t5_numbers_gcd")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/t5_numbers_gcd")
```

You can then use this model to solve algebra 1d equations into numbers.

```python
query = "What is the highest common factor of 4210884 and 72?"
input_text = f"{query} </s>"
features = tokenizer([input_text], return_tensors='pt')
model.to('cuda')
output = model.generate(input_ids=features['input_ids'].cuda(), 
                        attention_mask=features['attention_mask'].cuda())

tokenizer.decode(output[0])
# <pad> 36</s>
```

Another examples:

+ Calculate the greatest common factor of 3470 and 97090. 
+ Answer:  10 Pred:  10
----
+ Calculate the highest common factor of 3480 and 775431.
+ Answer:  87 Pred:  87
----
+ What is the highest common divisor of 26 and 88049? 
+ Answer:  13 Pred:  13
----
+ Calculate the highest common factor of 1416 and 24203688.
+ Answer:  1416 Pred:  1416
----
+ Calculate the highest common divisor of 124 and 69445828. 
+ Answer:  124 Pred:  124
----
+ What is the greatest common factor of 657906 and 470?
+ Answer:  94 Pred:  94
----
+ What is the highest common factor of 4210884 and 72?
+ Answer:  36 Pred:  36

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/MathLM)
> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)
