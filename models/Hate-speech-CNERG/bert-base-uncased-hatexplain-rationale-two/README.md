---
language: en
license: apache-2.0
datasets:
  - hatexplain
---

The model is used for classifying a text as Abusive (Hatespeech and Offensive) or Normal. The model is trained using data from Gab and Twitter and Human Rationales were included as part of the training data to boost the performance. The model also has a rationale predictor head that can predict the rationales given an abusive sentence.                                                                                                    
 
The dataset and models are available here: https://github.com/punyajoy/HateXplain

**Details of usage**

Please use the **Model_Rational_Label** class inside [models.py](models.py) to load the models. The default prediction in this hosted inference API may be wrong due to the use of different class initialisations.

~~~
from transformers import AutoTokenizer, AutoModelForSequenceClassification
### from models.py
from models import *
tokenizer = AutoTokenizer.from_pretrained("Hate-speech-CNERG/bert-base-uncased-hatexplain-rationale-two")
model = Model_Rational_Label.from_pretrained("Hate-speech-CNERG/bert-base-uncased-hatexplain-rationale-two")
inputs = tokenizer('He is a great guy", return_tensors="pt")
prediction_logits, _ = model(input_ids=inputs['input_ids'],attention_mask=inputs['attention_mask'])
~~~

**For more details about our paper**

Binny Mathew, Punyajoy Saha, Seid Muhie Yimam, Chris Biemann, Pawan Goyal, and Animesh Mukherjee "[HateXplain: A Benchmark Dataset for Explainable Hate Speech Detection)". Accepted at AAAI 2021.

***Please cite our paper in any published work that uses any of these resources.***
~~~

@article{mathew2020hatexplain,
  title={HateXplain: A Benchmark Dataset for Explainable Hate Speech Detection},
  author={Mathew, Binny and Saha, Punyajoy and Yimam, Seid Muhie and Biemann, Chris and Goyal, Pawan and Mukherjee, Animesh},
  journal={arXiv preprint arXiv:2012.10289},
  year={2020}

}

~~~




