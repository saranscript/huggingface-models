# algebra_linear_1d
---
language: en
datasets:
- algebra_linear_1d
---

This is a [t5-small](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) fine-tuned version on the [math_dataset/algebra_linear_1d](https://www.tensorflow.org/datasets/catalog/math_dataset#mathdatasetalgebra_linear_1d_default_config) for solving **algebra 1d equations** mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/algebra_linear_1d")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/algebra_linear_1d")
```

You can then use this model to solve algebra 1d equations into numbers.

```python
query = "Solve 0 = 1026*x - 2474 + 46592 for x"
input_text = f"{query} </s>"
features = tokenizer([input_text], return_tensors='pt')
model.to('cuda')
output = model.generate(input_ids=features['input_ids'].cuda(), 
                        attention_mask=features['attention_mask'].cuda())

tokenizer.decode(output[0])
# <pad> -41</s>
```

Another examples:

+ Solve 1112*r + 1418*r - 5220 = 587*r - 28536 for r. 
+ Answer:  -12 Pred:  -12
----
+ Solve -119*k + 6*k - 117 - 352 = 322 for k. 
+ Answer:  -7 Pred:  -7
----
+ Solve -547 = -62*t + 437 - 798 for t. 
+ Answer:  3 Pred:  3
----
+ Solve 3*j - 3*j + 0*j - 4802 = 98*j for j. 
+ Answer:  -49 Pred:  -49
----
+ Solve 3047*n - 6130*n - 1700 = -3049*n for n. 
+ Answer:  -50 Pred:  -50
----
+ Solve 121*i + 1690 = 76*i - 128*i + 133 for i. 
+ Answer:  -9 Pred:  -9

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/MathLM)
> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)
