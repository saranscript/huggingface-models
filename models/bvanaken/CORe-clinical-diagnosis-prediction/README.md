---
language: "en"
tags:
- bert
- medical
- clinical
- diagnosis
thumbnail: "https://core.app.datexis.com/static/paper.png"
---

# CORe Model - Clinical Diagnosis Prediction

## Model description

The CORe (_Clinical Outcome Representations_) model is introduced in the paper [Clinical Outcome Predictions from Admission Notes using Self-Supervised Knowledge Integration](https://www.aclweb.org/anthology/2021.eacl-main.75.pdf).
It is based on BioBERT and further pre-trained on clinical notes, disease descriptions and medical articles with a specialised _Clinical Outcome Pre-Training_ objective.

This model checkpoint is **fine-tuned on the task of diagnosis prediction**.
The model expects patient admission notes as input and outputs multi-label ICD9-code predictions.

#### Model Predictions
The model makes predictions on a total of 9237 labels. These contain 3- and 4-digit ICD9 codes and textual descriptions of these codes. The 4-digit codes and textual descriptions help to incorporate further topical and hierarchical information into the model during training (see Section 4.2 _ICD+: Incorporation of ICD Hierarchy_ in our paper). We recommend to only use the **3-digit code predictions at inference time**, because only those have been evaluated in our work.

#### How to use CORe Diagnosis Prediction

You can load the model via the transformers library:
```
from transformers import AutoTokenizer, AutoModelForSequenceClassification
tokenizer = AutoTokenizer.from_pretrained("bvanaken/CORe-clinical-diagnosis-prediction")
model = AutoModelForSequenceClassification.from_pretrained("bvanaken/CORe-clinical-diagnosis-prediction")
```

The following code shows an inference example:

```
input = "CHIEF COMPLAINT: Headaches\n\nPRESENT ILLNESS: 58yo man w/ hx of hypertension, AFib on coumadin presented to ED with the worst headache of his life."

tokenized_input = tokenizer(input, return_tensors="pt")
output = model(**tokenized_input)

import torch
predictions = torch.sigmoid(output.logits)
predicted_labels = [model.config.id2label[_id] for _id in (predictions > 0.3).nonzero()[:, 1].tolist()]
```
Note: For the best performance, we recommend to determine the thresholds (0.3 in this example) individually per label.


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