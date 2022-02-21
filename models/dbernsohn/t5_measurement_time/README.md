# measurement_time
---
language: en
datasets:
- measurement_time
---

This is a [t5-small](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) fine-tuned version on the [math_dataset/measurement_time](https://www.tensorflow.org/datasets/catalog/math_dataset#mathdatasetmeasurement_time) for solving **measurement time equations** mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/t5_measurement_time")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/t5_measurement_time")
```

You can then use this model to solve algebra 1d equations into numbers.

```python
query = "How many minutes are there between 2:09 PM and 2:27 PM?"
input_text = f"{query} </s>"
features = tokenizer([input_text], return_tensors='pt')
model.to('cuda')
output = model.generate(input_ids=features['input_ids'].cuda(), 
                        attention_mask=features['attention_mask'].cuda())

tokenizer.decode(output[0])
# <pad> 18</s>
```

Another examples:

+ How many minutes are there between 2:09 PM and 2:27 PM?
+ Answer:  18 Pred:  18
----
+ What is 116 minutes after 10:06 AM?
+ Answer:  12:02 PM Pred:  12:02 PM
----
+ What is 608 minutes after 3:14 PM?
+ Answer:  1:22 AM Pred:  1:22 AM
----
+ What is 64 minutes before 9:16 AM?
+ Answer:  8:12 AM Pred:  8:12 AM
----
+ What is 427 minutes before 4:27 AM?
+ Answer:  9:20 PM Pred:  9:20 PM
----
+ How many minutes are there between 6:36 PM and 12:15 AM?
+ Answer:  339 Pred:  339
----
+ What is 554 minutes before 5:24 PM?
+ Answer:  8:10 AM Pred:  8:10 AM
----
+ What is 307 minutes after 5:15 AM?
+ Answer:  10:22 AM Pred:  10:22 AM

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/MathLM)
> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)
