---
language: ar
tags:
- pytorch
- tf
- QARiB
- qarib
datasets:
- arabic_billion_words
- open_subtitles
- twitter
metrics:
- f1
widget:
 - text: " شو عندكم يا [MASK] ."
---
# QARiB: QCRI Arabic and Dialectal BERT

## About QARiB
QCRI Arabic and Dialectal BERT  (QARiB) model, was trained on a collection of ~ 420 Million tweets and ~ 180 Million sentences of text.
For the tweets, the data was collected using twitter API and using language filter. `lang:ar`. For the text data, it was a combination from
[Arabic GigaWord](url), [Abulkhair Arabic Corpus]() and [OPUS](http://opus.nlpl.eu/).

QARiB: Is the Arabic name for "Boat".

## Model and Parameters:

- Data size: 14B tokens
- Vocabulary: 64k
- Iterations:  10M
- Number of Layers: 12

## Training QARiB
See details in [Training QARiB](https://github.com/qcri/QARIB/Training_QARiB.md)

## Using QARiB

You can use the raw model for either masked language modeling or next sentence prediction, but it's mostly intended to be fine-tuned on a downstream task. See the model hub to look for fine-tuned versions on a task that interests you. For more details, see [Using QARiB](https://github.com/qcri/QARIB/Using_QARiB.md)

### How to use
You can use this model directly with a pipeline for masked language modeling:

```python
>>>from transformers import pipeline
>>>fill_mask = pipeline("fill-mask", model="./models/data60gb_86k")

>>> fill_mask("شو عندكم يا [MASK]")
[{'sequence': '[CLS] شو عندكم يا عرب [SEP]', 'score': 0.0990147516131401, 'token': 2355, 'token_str': 'عرب'}, 
{'sequence': '[CLS] شو عندكم يا جماعة [SEP]', 'score': 0.051633741706609726, 'token': 2308, 'token_str': 'جماعة'}, 
{'sequence': '[CLS] شو عندكم يا شباب [SEP]', 'score': 0.046871256083250046, 'token': 939, 'token_str': 'شباب'}, 
{'sequence': '[CLS] شو عندكم يا رفاق [SEP]', 'score': 0.03598872944712639, 'token': 7664, 'token_str': 'رفاق'}, 
{'sequence': '[CLS] شو عندكم يا ناس [SEP]', 'score': 0.031996358186006546, 'token': 271, 'token_str': 'ناس'}
]
>>> fill_mask("وقام المدير [MASK]")
[
{'sequence': '[CLS] وقام المدير بالعمل [SEP]', 'score': 0.0678194984793663, 'token': 4230, 'token_str': 'بالعمل'}, 
{'sequence': '[CLS] وقام المدير بذلك [SEP]', 'score': 0.05191086605191231, 'token': 984, 'token_str': 'بذلك'}, 
{'sequence': '[CLS] وقام المدير بالاتصال [SEP]', 'score': 0.045264165848493576, 'token': 26096, 'token_str': 'بالاتصال'}, 
{'sequence': '[CLS] وقام المدير بعمله [SEP]', 'score': 0.03732728958129883, 'token': 40486, 'token_str': 'بعمله'}, 
{'sequence': '[CLS] وقام المدير بالامر [SEP]', 'score': 0.0246378555893898, 'token': 29124, 'token_str': 'بالامر'}
]
>>> fill_mask("وقامت المديرة [MASK]")

[{'sequence': '[CLS] وقامت المديرة بذلك [SEP]', 'score': 0.23992691934108734, 'token': 984, 'token_str': 'بذلك'}, 
{'sequence': '[CLS] وقامت المديرة بالامر [SEP]', 'score': 0.108805812895298, 'token': 29124, 'token_str': 'بالامر'}, 
{'sequence': '[CLS] وقامت المديرة بالعمل [SEP]', 'score': 0.06639821827411652, 'token': 4230, 'token_str': 'بالعمل'}, 
{'sequence': '[CLS] وقامت المديرة بالاتصال [SEP]', 'score': 0.05613093823194504, 'token': 26096, 'token_str': 'بالاتصال'}, 
{'sequence': '[CLS] وقامت المديرة المديرة [SEP]', 'score': 0.021778125315904617, 'token': 41635, 'token_str': 'المديرة'}]

>>> fill_mask("قللي وشفيييك يرحم [MASK]")
[{'sequence': '[CLS] قللي وشفيييك يرحم والديك [SEP]', 'score': 0.4152909517288208, 'token': 9650, 'token_str': 'والديك'}, 
{'sequence': '[CLS] قللي وشفيييك يرحملي [SEP]', 'score': 0.07663793861865997, 'token': 294, 'token_str': '##لي'}, 
{'sequence': '[CLS] قللي وشفيييك يرحم حالك [SEP]', 'score': 0.0453166700899601, 'token': 2663, 'token_str': 'حالك'}, 
{'sequence': '[CLS] قللي وشفيييك يرحم امك [SEP]', 'score': 0.04390475153923035, 'token': 1942, 'token_str': 'امك'}, 
{'sequence': '[CLS] قللي وشفيييك يرحمونك [SEP]', 'score': 0.027349254116415977, 'token': 3283, 'token_str': '##ونك'}]


```

## Evaluations:

|**Experiment** |**mBERT**|**AraBERT0.1**|**AraBERT1.0**|**ArabicBERT**|**QARiB**|
|---------------|---------|--------------|--------------|--------------|---------|
|Dialect Identification | 6.06% | 59.92% | 59.85% | 61.70% | **65.21%** |
|Emotion Detection | 27.90% | 43.89% | 42.37% | 41.65% | **44.35%** |
|Named-Entity Recognition (NER) | 49.38% | 64.97% | **66.63%** | 64.04% | 61.62% |
|Offensive Language Detection | 83.14% | 88.07% | 88.97% | 88.19% | **91.94%** |
|Sentiment Analysis | 86.61% | 90.80% | **93.58%** | 83.27% | 93.31% |

## Model Weights and Vocab Download

From Huggingface site: https://huggingface.co/qarib/bert-base-qarib

## Contacts

Ahmed Abdelali, Sabit Hassan, Hamdy Mubarak, Kareem Darwish and Younes Samih

## Reference
```
@article{abdelali2021pretraining,
    title={Pre-Training BERT on Arabic Tweets: Practical Considerations},
    author={Ahmed Abdelali and Sabit Hassan and Hamdy Mubarak and Kareem Darwish and Younes Samih},
    year={2021},
    eprint={2102.10684},
    archivePrefix={arXiv},
    primaryClass={cs.CL}
}
```


