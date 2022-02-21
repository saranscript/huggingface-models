---
language: bn
tags:
- mbert
- bengali
- question-answering
- bangla
- qa
license: mit
datasets:
- tydiqa
---

# mBERT Bengali Question Answering
`mBERT-Bengali-Tydiqa-QA` is a question answering model fine-tuning [bert-base-multilingual-uncased](https://huggingface.co/bert-base-multilingual-uncased) model with [tydiqa](https://github.com/google-research-datasets/tydiqa) Bengali datasets.


## Usage
You can use [bntransformer](https://github.com/sagorbrur/bntransformer)

### Installation
`pip install bntransformer`

### Generate Answer

```py
from bntransformer import BanglaQA

bnqa = BanglaQA()
# you can custom model path or other bengali huggingface model path
# default it takes "sagorsarker/mbert-bengali-tydiqa-qa"
context = "সূর্য সেন ১৮৯৪ সালের ২২ মার্চ চট্টগ্রামের রাউজান থানার নোয়াপাড়ায় অর্থনৈতিক ভাবে অস্বচ্ছল পরিবারে জন্মগ্রহণ করেন। তাঁর পিতার নাম রাজমনি সেন এবং মাতার নাম শশী বালা সেন। রাজমনি সেনের দুই ছেলে আর চার মেয়ে। সূর্য সেন তাঁদের পরিবারের চতুর্থ সন্তান। দুই ছেলের নাম সূর্য ও কমল। চার মেয়ের নাম বরদাসুন্দরী, সাবিত্রী, ভানুমতী ও প্রমিলা। শৈশবে পিতা মাতাকে হারানো সূর্য সেন কাকা গৌরমনি সেনের কাছে মানুষ হয়েছেন। সূর্য সেন ছেলেবেলা থেকেই খুব মনোযোগী ভাল ছাত্র ছিলেন এবং ধর্মভাবাপন্ন গম্ভীর প্রকৃতির ছিলেন।"
question = "মাস্টারদা সূর্যকুমার সেনের বাবার নাম কী ছিল ?"

answers = bnqa.find_answer(context, question)
print(answers)

```

or

### Transformers QA Pipeline

```py
from transformers import AutoModelForQuestionAnswering, AutoTokenizer, pipeline

model_name = "sagorsarker/mbert-bengali-tydiqa-qa"
model = AutoModelForQuestionAnswering.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)

nlp = pipeline('question-answering', model=model_name, tokenizer=model_name)
qa_input = {
    'question': 'মাস্টারদা সূর্যকুমার সেনের বাবার নাম কী ছিল ?',
    'context': 'সূর্য সেন ১৮৯৪ সালের ২২ মার্চ চট্টগ্রামের রাউজান থানার নোয়াপাড়ায় অর্থনৈতিক ভাবে অস্বচ্ছল পরিবারে জন্মগ্রহণ করেন। তাঁর পিতার নাম রাজমনি সেন এবং মাতার নাম শশী বালা সেন। রাজমনি সেনের দুই ছেলে আর চার মেয়ে। সূর্য সেন তাঁদের পরিবারের চতুর্থ সন্তান। দুই ছেলের নাম সূর্য ও কমল। চার মেয়ের নাম বরদাসুন্দরী, সাবিত্রী, ভানুমতী ও প্রমিলা। শৈশবে পিতা মাতাকে হারানো সূর্য সেন কাকা গৌরমনি সেনের কাছে মানুষ হয়েছেন। সূর্য সেন ছেলেবেলা থেকেই খুব মনোযোগী ভাল ছাত্র ছিলেন এবং ধর্মভাবাপন্ন গম্ভীর প্রকৃতির ছিলেন।'
}
result = nlp(qa_input)
print(result)

```


## Training Details
- `mBERT-Bengali-Tydiqa-QA`  model build using [bert-base-multilingual-uncased](https://huggingface.co/bert-base-multilingual-uncased)
- `mBERT-Bengali-Tydiqa-QA` model trained with [tydiqa](https://github.com/google-research-datasets/tydiqa) Bengali datasets.
- Tydiqa Bengali data contains **2390 train** data and **113 validation** data
- `mBERT-Bengali-Tydiqa-QA` model trained in [kaggle](https://www.kaggle.com/) GPU
- `mBERT-Bengali-Tydiqa-QA` model trained total 5 epochs
- `mBERT-Bengali-Tydiqa-QA` trained using [transformers/example/question-aswering](https://colab.research.google.com/github/huggingface/notebooks/blob/master/examples/question_answering.ipynb) notebook with all default settings except pre-trained model and datasets part


## Evaluation Results
Here is the training evaluation part
```
Exact Match: 57.52212389380531
F1 Score: 68.66183963529096

```

## Authors
- Sagor Sarker
  - [Github](https://github.com/sagorbrur)
  - [LinkedIn](https://www.linkedin.com/in/sagor-sarker/)