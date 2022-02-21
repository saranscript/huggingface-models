# Part of Speech tagging Model for Telugu

#### How to use
Use the below script from your python terminal as the web interface for inference has few encoding issues for Telugu

PS: If you find my model useful, I would appreciate a note from you as it would encourage me to continue improving it and also add new models.

```python
from simpletransformers.ner import NERModel
model = NERModel('bert',
                 'kuppuluri/telugu_bertu_pos',
                 args={"use_multiprocessing": False},
                 labels=[
                     'QC', 'JJ', 'NN', 'QF', 'RDP', 'O',
                     'NNO', 'PRP', 'RP', 'VM', 'WQ',
                     'PSP', 'UT', 'CC', 'INTF', 'SYMP',
                     'NNP', 'INJ', 'SYM', 'CL', 'QO',
                     'DEM', 'RB', 'NST', ],
                 use_cuda=False)

text = "విరాట్ కోహ్లీ కూడా అదే నిర్లక్ష్యాన్ని ప్రదర్శించి కేవలం ఒక పరుగుకే రనౌటై పెవిలియన్ చేరాడు ."
results = model.predict([text])
```

## Training data

Training data is from https://github.com/anikethjr/NER_Telugu

## Eval results

On the test set my results were

eval_loss = 0.0036797842364565416

f1_score = 0.9983795127912227

precision = 0.9984325602401637

recall = 0.9983264709788816
