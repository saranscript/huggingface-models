---
license: mit
---

# diwank/dyda-deberta-pair

Deberta-based Daily Dialog style dialog-act annotations classification model. It takes two sentences as inputs (one previous and one current of a dialog). The previous sentence can be an empty string if this is the first utterance of a speaker in a dialog. Outputs one of four labels (exactly as in the [daily-dialog dataset](https://huggingface.co/datasets/daily_dialog) ): *__dummy__ (0), inform (1), question (2), directive (3), commissive (4)*

## Usage

```python
from simpletransformers.classification import (
    ClassificationModel, ClassificationArgs
)

model = ClassificationModel("deberta", "diwank/dyda-deberta-pair")
convert_to_label = lambda n: ["__dummy__ (0), inform (1), question (2), directive (3), commissive (4)".split(', ')[i] for i in n]

predictions, raw_outputs = model.predict([["Say what is the meaning of life?", "I dont know"]])
convert_to_label(predictions)  # inform (1)
```