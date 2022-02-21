# algebra_linear_1d_composed
---
language: en
datasets:
- algebra_linear_1d_composed
---

This is a [t5-small](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) fine-tuned version on the [math_dataset/algebra_linear_1d_composed](https://www.tensorflow.org/datasets/catalog/math_dataset#mathdatasetalgebra_linear_1d_composed) for solving **algebra linear 1d composed equations** mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/algebra_linear_1d_composed")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/algebra_linear_1d_composed")
```

You can then use this model to solve algebra 1d equations into numbers.

```python
query = "Suppose -d = 5 - 16. Let b = -579 + 584. Solve -b*c + 36 = d for c."
input_text = f"{query} </s>"
features = tokenizer([input_text], return_tensors='pt')
model.to('cuda')
output = model.generate(input_ids=features['input_ids'].cuda(), 
                        attention_mask=features['attention_mask'].cuda())

tokenizer.decode(output[0])
# <pad> 5</s>
```

Another examples:

+ Suppose -d = 5 - 16. Let b = -579 + 584. Solve -b*c + 36 = d for c.
+ Answer:  5 Pred:  5
----
+ Suppose 3*v - l + 9 = 4*v, 0 = -5*v + 5*l - 5. Let f(s) = 3*s**2 + 1. Let g be f(-1). Suppose 63 = g*x - x. Solve -5*i + v + x = 0 for i.
+ Answer:  5 Pred:  5
----
+ Let w be 2 - (0 - 0)/(-2). Let f = -110 - -110. Suppose f*m - 4*m + 3*m = 0. Solve m*v = -w*v for v.
+ Answer:  0 Pred:  0
----
+ Let a(h) = -34*h**3 - 15 + 3*h + 36*h**3 + 8*h**2 + 5*h**2. Let r be a(-6). Solve 2*z = r*z for z.
+ Answer:  0 Pred:  0
----
+ Suppose -3*p + 24 = -3*c, 0*c + 6 = -2*c. Suppose -67 = 4*i + 289. Let t = i + 94. Solve t = 2*y - p for y.
+ Answer:  5 Pred:  5
----
+ Let b = -36 + 53. Suppose -7*u - b = -73. Solve j + 3*j = -u for j.
+ Answer:  -2 Pred:  -2
----
+ Let h be 8*((-2)/2 + 14)*1. Let y = -101 + h. Solve y*p = -p for p.
+ Answer:  0 Pred:  0
----
+ Let b = 178 - 79. Let s be 9/(-1 - 2 - b/(-22)). Solve s = -k - k for k.
+ Answer:  -3 Pred:  -3
----
+ Suppose 31 = -4*z + 11, -3*k - 5*z - 22 = 0. Solve 23 = -11*p + k for p.
+ Answer:  -2 Pred:  -2

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/MathLM)
> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)
