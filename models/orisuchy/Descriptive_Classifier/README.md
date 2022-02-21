---
license: afl-3.0
language: "he"
tags:
- Text Classification
widget:
- text: "היער השחור והגדול"
- text: "ואז הוא הלך לטייל בתוך היער השחור והגדול"

---
## How to Use the model:
```python
from transformers import pipeline
classifier = pipeline("text-classification",model='orisuchy/Descriptive_Classifier', return_all_scores=True)
outputs = classifier("מסווג חתיך במיוחד")
print(outputs)

"""
Output:
[[
{'label': 'Descriptive', 'score': 0.9996114373207092},
{'label': 'Might Descriptive', 'score': 7.421540794894099e-05},
{'label': 'Not Descriptive', 'score': 0.0003142959321849048}]]
"""
```
#### Or, if you want only the final class:
```python
from transformers import pipeline
classifier = pipeline("text-classification",model='orisuchy/Descriptive_Classifier')
output = classifier("הלכתי אליו הביתה וחיכיתי")
print(output)

"""
Output:
[{'label': 'Not Descriptive', 'score': 0.9998830556869507}]
"""
```