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
- Farasa
metrics:
- f1
widget:
 - text: "و+قام ال+مدير [MASK]"
---
# QARiB: QCRI Arabic and Dialectal BERT
## About QARiB Farasa
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

This model expects the data to be segmented. You may use [Farasa Segmenter](https://farasa-api.qcri.org/segmentation/) API.

### How to use
You can use this model directly with a pipeline for masked language modeling:
```python
>>>from transformers import pipeline
>>>fill_mask = pipeline("fill-mask", model="./models/bert-base-qarib_far")
>>> fill_mask("و+قام ال+مدير [MASK]")
[

]
>>> fill_mask("و+قام+ت ال+مدير+ة [MASK]")
[
]
>>> fill_mask("قللي وشفيييك يرحم [MASK]")
[
]
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
From Huggingface site: https://huggingface.co/qarib/bert-base-qarib_far
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