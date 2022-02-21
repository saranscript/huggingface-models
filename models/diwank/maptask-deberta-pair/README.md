---
license: mit
---

# maptask-deberta-pair
Deberta-based Daily MapTask style dialog-act annotations classification model

## Example

```python
from simpletransformers.classification import (
    ClassificationModel, ClassificationArgs
)

model = ClassificationModel("deberta", "diwank/maptask-deberta-pair")

predictions, raw_outputs = model.predict([["Say what is the meaning of life?", "I dont know"]])

convert_to_label = lambda n: ["acknowledge (0), align (1), check (2), clarify (3), explain (4), instruct (5), query_w (6), query_yn (7), ready (8), reply_n (9), reply_w (10), reply_y (11)".split(', ')[i] for i in n]

convert_to_label(predictions) # reply_n (9)
```