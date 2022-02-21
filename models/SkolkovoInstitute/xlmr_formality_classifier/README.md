---
language:
- en
- fr
- it
- pt

tags:
- formal or informal classification

licenses:
- cc-by-nc-sa
---

XLMRoberta-based classifier trained on XFORMAL.


all

|              | precision | recall   | f1-score | support |
|--------------|-----------|----------|----------|---------|
| 0            | 0.744912  | 0.927790 | 0.826354 | 108019  |
| 1            | 0.889088  | 0.645630 | 0.748048 | 96845   |
| accuracy     |           |          | 0.794405 | 204864  |
| macro avg    | 0.817000  | 0.786710 | 0.787201 | 204864  |
| weighted avg | 0.813068  | 0.794405 | 0.789337 | 204864  |


en

|              | precision | recall   | f1-score | support |
|--------------|-----------|----------|----------|---------|
| 0            | 0.800053  | 0.962981 | 0.873988 | 22151   |
| 1            | 0.945106  | 0.725899 | 0.821124 | 19449   |
| accuracy     |           |          | 0.852139 | 41600   |
| macro avg    | 0.872579  | 0.844440 | 0.847556 | 41600   |
| weighted avg | 0.867869  | 0.852139 | 0.849273 | 41600   |

fr

|              | precision | recall   | f1-score | support |
|--------------|-----------|----------|----------|---------|
| 0            | 0.746709  | 0.925738 | 0.826641 | 21505   |
| 1            | 0.887305  | 0.650592 | 0.750731 | 19327   |
| accuracy     |           |          | 0.795504 | 40832   |
| macro avg    | 0.817007  | 0.788165 | 0.788686 | 40832   |
| weighted avg | 0.813257  | 0.795504 | 0.790711 | 40832   |

it

|              | precision | recall   | f1-score | support |
|--------------|-----------|----------|----------|---------|
| 0            | 0.721282  | 0.914669 | 0.806545 | 21528   |
| 1            | 0.864887  | 0.607135 | 0.713445 | 19368   |
| accuracy     |           |          | 0.769024 | 40896   |
| macro avg    | 0.793084  | 0.760902 | 0.759995 | 40896   |
| weighted avg | 0.789292  | 0.769024 | 0.762454 | 40896   |

pt

|              | precision | recall   | f1-score | support |
|--------------|-----------|----------|----------|---------|
| 0            | 0.717546  | 0.908167 | 0.801681 | 21637   |
| 1            | 0.853628  | 0.599700 | 0.704481 | 19323   |
| accuracy     |           |          | 0.762646 | 40960   |
| macro avg    | 0.785587  | 0.753933 | 0.753081 | 40960   |
| weighted avg | 0.781743  | 0.762646 | 0.755826 | 40960   |

## How to use
```python
from transformers import XLMRobertaTokenizerFast, XLMRobertaForSequenceClassification

# load tokenizer and model weights
tokenizer = XLMRobertaTokenizerFast.from_pretrained('SkolkovoInstitute/xlmr_formality_classifier')
model = XLMRobertaForSequenceClassification.from_pretrained('SkolkovoInstitute/xlmr_formality_classifier')

# prepare the input
batch = tokenizer.encode('ты супер', return_tensors='pt')

# inference
model(batch)
```


## Licensing Information

[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png