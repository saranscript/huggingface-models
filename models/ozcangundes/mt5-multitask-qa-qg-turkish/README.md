---
language: tr
datasets:
- TQUAD
tags: 
- question-answering
- question-generation
- multitask-model

license: apache-2.0
---

# mT5-small based Turkish Multitask (Answer Extraction, Question Generation and Question Answering) System

[Google's Multilingual T5-small](https://github.com/google-research/multilingual-t5) is fine-tuned on [Turkish Question Answering dataset](https://github.com/okanvk/Turkish-Reading-Comprehension-Question-Answering-Dataset) for three downstream task **Answer extraction, Question Generation and Question Answering** served in this single model. mT5 model was also trained for multiple text2text NLP tasks. 

All data processing, training and pipeline codes can be found on my [Github](https://github.com/ozcangundes/multitask-question-generation). I will share the training details in the repo as soon as possible. 

mT5 small model has 300 million parameters and model size is about 1.2GB. Therefore, it takes significant amount of time to fine tune it. 

8 epoch and 1e-4 learning rate with 0 warmup steps was applied during training. These hparams and the others can be fine-tuned for much more better results.

## Requirements ❗❗❗
```
!pip install transformers==4.4.2
!pip install sentencepiece==0.1.95
!git clone https://github.com/ozcangundes/multitask-question-generation.git
%cd multitask-question-generation/
```

## Usage 🚀🚀
```
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
tokenizer = AutoTokenizer.from_pretrained("ozcangundes/mt5-multitask-qa-qg-turkish") 
model = AutoModelForSeq2SeqLM.from_pretrained("ozcangundes/mt5-multitask-qa-qg-turkish")

from pipelines import pipeline #pipelines.py script in the cloned repo
multimodel = pipeline("multitask-qa-qg",tokenizer=tokenizer,model=model)

#sample text
text="Özcan Gündeş, 1993 yılı Tarsus doğumludur. Orta Doğu Teknik Üniversitesi \\\\
Endüstri Mühendisliği bölümünde 2011 2016 yılları arasında lisans eğitimi görmüştür. \\\\
Yüksek lisansını ise 2020 Aralık ayında, 4.00 genel not ortalaması ile \\\\
Boğaziçi Üniversitesi, Yönetim Bilişim Sistemleri bölümünde tamamlamıştır.\\\\
Futbolla yakından ilgilenmekle birlikte, Galatasaray kulübü taraftarıdır."
```

## Example - Both Question Generation and Question Answering 💬💬
```
multimodel(text)

#output
=> [{'answer': 'Tarsus', 'question': 'Özcan Gündeş nerede doğmuştur?'},
 {'answer': '1993', 'question': 'Özcan Gündeş kaç yılında doğmuştur?'},
 {'answer': '2011 2016',
  'question': 'Özcan Gündeş lisans eğitimini hangi yıllar arasında tamamlamıştır?'},
 {'answer': 'Boğaziçi Üniversitesi, Yönetim Bilişim Sistemleri',
  'question': 'Özcan Gündeş yüksek lisansını hangi bölümde tamamlamıştır?'},
 {'answer': 'Galatasaray kulübü',
  'question': 'Özcan Gündeş futbolla yakından ilgilenmekle birlikte hangi kulübü taraftarıdır?'}]
```
From this text, 5 questions are generated and they are answered by the model. 

## Example - Question Answering 💭💭

Both text and also, related question should be passed into pipeline.
```
multimodel({"context":text,"question":"Özcan hangi takımı tutmaktadır?"})

#output
=> Galatasaray

multimodel({"context":text,"question":"Özcan, yüksek lisanstan ne zaman mezun oldu?"})

#output
=> 2020 Aralık ayında


multimodel({"context":text,"question":"Özcan'ın yüksek lisans bitirme notu kaçtır?"})

#output
=> 4.00 

#Sorry for being cocky 😝😝
```

## ACKNOWLEDGEMENT

This work is inspired from [Suraj Patil's great repo](https://github.com/patil-suraj/question_generation). I would like to thank him for the clean codes and also,[Okan Çiftçi](https://github.com/okanvk) for the Turkish dataset 🙏

