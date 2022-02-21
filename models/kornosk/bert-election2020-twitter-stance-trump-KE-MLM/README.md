---
language: "en"
tags:
- twitter
- stance-detection
- election2020
license: "gpl-3.0"
---

# Pre-trained BERT on Twitter US Election 2020 for Stance Detection towards Donald Trump (KE-MLM)

Pre-trained weights for **KE-MLM model** in [Knowledge Enhance Masked Language Model for Stance Detection](https://www.aclweb.org/anthology/2021.naacl-main.376), NAACL 2021.

# Training Data

This model is pre-trained on over 5 million English tweets about the 2020 US Presidential Election. Then fine-tuned using our [stance-labeled data](https://github.com/GU-DataLab/stance-detection-KE-MLM) for stance detection towards Donald Trump.

# Training Objective

This model is initialized with BERT-base and trained with normal MLM objective with classification layer fine-tuned for stance detection towards Donald Trump.

# Usage

This pre-trained language model is fine-tuned to the stance detection task specifically for Donald Trump.

Please see the [official repository](https://github.com/GU-DataLab/stance-detection-KE-MLM) for more detail.

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch
import numpy as np

# choose GPU if available
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

# select mode path here
pretrained_LM_path = "kornosk/bert-election2020-twitter-stance-trump-KE-MLM"

# load model
tokenizer = AutoTokenizer.from_pretrained(pretrained_LM_path)
model = AutoModelForSequenceClassification.from_pretrained(pretrained_LM_path)

id2label = {
    0: "AGAINST",
    1: "FAVOR",
    2: "NONE"
}

##### Prediction Neutral #####
sentence = "Hello World."
inputs = tokenizer(sentence.lower(), return_tensors="pt")
outputs = model(**inputs)
predicted_probability = torch.softmax(outputs[0], dim=1)[0].tolist()

print("Sentence:", sentence)
print("Prediction:", id2label[np.argmax(predicted_probability)])
print("Against:", predicted_probability[0])
print("Favor:", predicted_probability[1])
print("Neutral:", predicted_probability[2])

##### Prediction Favor #####
sentence = "Go Go Trump!!!"
inputs = tokenizer(sentence.lower(), return_tensors="pt")
outputs = model(**inputs)
predicted_probability = torch.softmax(outputs[0], dim=1)[0].tolist()

print("Sentence:", sentence)
print("Prediction:", id2label[np.argmax(predicted_probability)])
print("Against:", predicted_probability[0])
print("Favor:", predicted_probability[1])
print("Neutral:", predicted_probability[2])

##### Prediction Against #####
sentence = "Trump is the worst."
inputs = tokenizer(sentence.lower(), return_tensors="pt")
outputs = model(**inputs)
predicted_probability = torch.softmax(outputs[0], dim=1)[0].tolist()

print("Sentence:", sentence)
print("Prediction:", id2label[np.argmax(predicted_probability)])
print("Against:", predicted_probability[0])
print("Favor:", predicted_probability[1])
print("Neutral:", predicted_probability[2])

# please consider citing our paper if you feel this is useful :)
```

# Reference

- [Knowledge Enhance Masked Language Model for Stance Detection](https://www.aclweb.org/anthology/2021.naacl-main.376), NAACL 2021.

# Citation
```bibtex
@inproceedings{kawintiranon2021knowledge,
    title={Knowledge Enhanced Masked Language Model for Stance Detection},
    author={Kawintiranon, Kornraphop and Singh, Lisa},
    booktitle={Proceedings of the 2021 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies},
    year={2021},
    publisher={Association for Computational Linguistics},
    url={https://www.aclweb.org/anthology/2021.naacl-main.376}
}
```