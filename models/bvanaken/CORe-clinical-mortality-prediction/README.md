---
language: "en"
tags:
- bert
- medical
- clinical
- mortality
thumbnail: "https://core.app.datexis.com/static/paper.png"
---

# CORe Model - Clinical Mortality Risk Prediction

## Model description

The CORe (_Clinical Outcome Representations_) model is introduced in the paper [Clinical Outcome Predictions from Admission Notes using Self-Supervised Knowledge Integration](https://www.aclweb.org/anthology/2021.eacl-main.75.pdf).
It is based on BioBERT and further pre-trained on clinical notes, disease descriptions and medical articles with a specialised _Clinical Outcome Pre-Training_ objective.

This model checkpoint is **fine-tuned on the task of mortality risk prediction**.
The model expects patient admission notes as input and outputs the predicted risk of in-hospital mortality.

#### How to use CORe Mortality Risk Prediction

You can load the model via the transformers library:
```
from transformers import AutoTokenizer, AutoModelForSequenceClassification
tokenizer = AutoTokenizer.from_pretrained("bvanaken/CORe-clinical-mortality-prediction")
model = AutoModelForSequenceClassification.from_pretrained("bvanaken/CORe-clinical-mortality-prediction")
```

The following code shows an inference example:

```
input = "CHIEF COMPLAINT: Headaches\n\nPRESENT ILLNESS: 58yo man w/ hx of hypertension, AFib on coumadin presented to ED with the worst headache of his life."

tokenized_input = tokenizer(input, return_tensors="pt")
output = model(**tokenized_input)

import torch
predictions = torch.softmax(output.logits.detach(), dim=1)
mortality_risk_prediction = predictions[0][1].item()
```


### More Information

For all the details about CORe and contact info, please visit [CORe.app.datexis.com](http://core.app.datexis.com/).

### Cite

```bibtex
@inproceedings{vanaken21,
  author    = {Betty van Aken and
               Jens-Michalis Papaioannou and
               Manuel Mayrdorfer and
               Klemens Budde and
               Felix A. Gers and
               Alexander Löser},
  title     = {Clinical Outcome Prediction from Admission Notes using Self-Supervised
               Knowledge Integration},
  booktitle = {Proceedings of the 16th Conference of the European Chapter of the
               Association for Computational Linguistics: Main Volume, {EACL} 2021,
               Online, April 19 - 23, 2021},
  publisher = {Association for Computational Linguistics},
  year      = {2021},
}
```