---
language:
- ru

tags:
- toxic comments classification

licenses:
- cc-by-nc-sa
---

Bert-based classifier (finetuned from [Conversational Rubert](https://huggingface.co/DeepPavlov/rubert-base-cased-conversational)) trained on merge of Russian Language Toxic Comments [dataset](https://www.kaggle.com/blackmoon/russian-language-toxic-comments/metadata) collected from 2ch.hk and Toxic Russian Comments [dataset](https://www.kaggle.com/alexandersemiletov/toxic-russian-comments) collected from ok.ru.

The datasets were merged, shuffled, and split into train, dev, test splits in 80-10-10 proportion.
The metrics obtained from test dataset is as follows

|              | precision | recall | f1-score | support |
|:------------:|:---------:|:------:|:--------:|:-------:|
|       0      |    0.98   |  0.99  |   0.98   | 21384   |
|       1      |    0.94   |  0.92  |   0.93   | 4886    |
|   accuracy   |       |   |   0.97  |         26270|
| macro avg    | 0.96      | 0.96   | 0.96     | 26270   |
| weighted avg | 0.97      | 0.97   | 0.97     | 26270   |


## How to use
```python
from transformers import BertTokenizer, BertForSequenceClassification

# load tokenizer and model weights
tokenizer = BertTokenizer.from_pretrained('SkolkovoInstitute/russian_toxicity_classifier')
model = BertForSequenceClassification.from_pretrained('SkolkovoInstitute/russian_toxicity_classifier')

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