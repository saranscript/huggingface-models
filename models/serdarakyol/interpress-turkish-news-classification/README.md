---
language: tr
Dataset: interpress_news_category_tr
---
# INTERPRESS NEWS CLASSIFICATION
## Dataset
The dataset downloaded from interpress. This dataset is real world data. Actually there are 273K data but I filtered them and used 108K data for this model. For more information about dataset please visit this [link](https://huggingface.co/datasets/interpress_news_category_tr_lite)

## Model
Model accuracy on train data and validation data is %97. The data split as %80 train and %20 validation. The results as shown as below

### Classification report
![Classification report](classification_report.png)

### Confusion matrix
![Confusion matrix](confusion_matrix.png)

## Usage for Torch
```sh
pip install transformers or pip install transformers==4.3.3
```
```sh
from transformers import AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("serdarakyol/interpress-turkish-news-classification")
model = AutoModelForSequenceClassification.from_pretrained("serdarakyol/interpress-turkish-news-classification")
```

```sh
import torch
import numpy as np

if torch.cuda.is_available():    
    device = torch.device("cuda")
    model = model.cuda()
    print('There are %d GPU(s) available.' % torch.cuda.device_count())
    print('GPU name is:', torch.cuda.get_device_name(0))
else:
    print('No GPU available, using the CPU instead.')
    device = torch.device("cpu")
```
```sh
def prediction(news):
    news=[news]
    indices=tokenizer.batch_encode_plus(
    news,
    max_length=512,
    add_special_tokens=True,
    return_attention_mask=True,
    padding='max_length',
    truncation=True,
    return_tensors='pt')

    inputs = indices["input_ids"].clone().detach().to(device)
    masks = indices["attention_mask"].clone().detach().to(device)

    with torch.no_grad():
        output = model(inputs, token_type_ids=None,attention_mask=masks)

    logits = output[0]
    logits = logits.detach().cpu().numpy()
    pred = np.argmax(logits,axis=1)[0]
    return pred
```
```sh
news = r"ABD'den Prens Selman'a yaptırım yok Beyaz Saray Sözcüsü Psaki, Muhammed bin Selman'a yaptırım uygulamamanın \"doğru karar\" olduğunu savundu. Psaki, \"Tarihimizde, Demokrat ve Cumhuriyetçi başkanların yönetimlerinde diplomatik ilişki içinde olduğumuz ülkelerin liderlerine yönelik yaptırım getirilmemiştir\" dedi."
```
You can find the news in this [link](https://www.ntv.com.tr/dunya/abdden-prens-selmana-yaptirim-yok,YTeWNv0-oU6Glbhnpjs1JQ) (news date: 02/03/2021)
```sh
labels = {
    0 : "Culture-Art",
    1 : "Economy",
    2 : "Politics",
    3 : "Education",
    4 : "World",
    5 : "Sport",
    6 : "Technology",
    7 : "Magazine",
    8 : "Health",
    9 : "Agenda"
}
pred = prediction(news)
print(labels[pred])
# > World
```
## Usage for Tensorflow
```sh
pip install transformers or pip install transformers==4.3.3

import tensorflow as tf
from transformers import BertTokenizer, TFBertForSequenceClassification
import numpy as np

tokenizer = BertTokenizer.from_pretrained('serdarakyol/interpress-turkish-news-classification')
model = TFBertForSequenceClassification.from_pretrained("serdarakyol/interpress-turkish-news-classification")

inputs = tokenizer(news, return_tensors="tf")
inputs["labels"] = tf.reshape(tf.constant(1), (-1, 1)) # Batch size 1

outputs = model(inputs)
loss = outputs.loss
logits = outputs.logits
pred = np.argmax(logits,axis=1)[0]
labels[pred]
# > World
```
Thanks to [@yavuzkomecoglu](https://huggingface.co/yavuzkomecoglu) for contributes

If you have any question, please, don't hesitate to contact with me
[![linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/serdarakyol55/)
[![Github](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/serdarakyol)