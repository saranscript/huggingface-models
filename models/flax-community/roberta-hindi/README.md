---
widget:
- text: "मुझे उनसे बात करना <mask> अच्छा लगा"
- text: "हम आपके सुखद <mask> की कामना करते हैं"
- text: "सभी अच्छी चीजों का एक <mask> होता है"
---

# RoBERTa base model for Hindi language

Pretrained model on Hindi language using a masked language modeling (MLM) objective. [A more interactive & comparison demo is available here](https://huggingface.co/spaces/flax-community/roberta-hindi).

> This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/pretrain-roberta-from-scratch-in-hindi/7091), organized by [Hugging Face](https://huggingface.co/) and TPU usage sponsored by Google.

## Model description

RoBERTa Hindi is a transformers model pretrained on a large corpus of Hindi data(a combination of **mc4, oscar and indic-nlp** datasets)

### How to use

You can use this model directly with a pipeline for masked language modeling:
```python
>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='flax-community/roberta-hindi')
>>> unmasker("हम आपके सुखद <mask> की कामना करते हैं")
[{'score': 0.3310680091381073,
  'sequence': 'हम आपके सुखद सफर की कामना करते हैं',
  'token': 1349,
  'token_str': ' सफर'},
 {'score': 0.15317578613758087,
  'sequence': 'हम आपके सुखद पल की कामना करते हैं',
  'token': 848,
  'token_str': ' पल'},
 {'score': 0.07826550304889679,
  'sequence': 'हम आपके सुखद समय की कामना करते हैं',
  'token': 453,
  'token_str': ' समय'},
 {'score': 0.06304813921451569,
  'sequence': 'हम आपके सुखद पहल की कामना करते हैं',
  'token': 404,
  'token_str': ' पहल'},
 {'score': 0.058322224766016006,
  'sequence': 'हम आपके सुखद अवसर की कामना करते हैं',
  'token': 857,
  'token_str': ' अवसर'}]
```

## Training data

The RoBERTa Hindi model was pretrained on the reunion of the following datasets:
- [OSCAR](https://huggingface.co/datasets/oscar) is a huge multilingual corpus obtained by language classification and filtering of the Common Crawl corpus using the goclassy architecture.
- [mC4](https://huggingface.co/datasets/mc4) is a multilingual colossal, cleaned version of Common Crawl's web crawl corpus.
- [IndicGLUE](https://indicnlp.ai4bharat.org/indic-glue/) is a natural language understanding benchmark.
- [Samanantar](https://indicnlp.ai4bharat.org/samanantar/) is a parallel corpora collection for Indic language.
- [Hindi Text Short and Large Summarization Corpus](https://www.kaggle.com/disisbig/hindi-text-short-and-large-summarization-corpus) is a collection of ~180k articles with their headlines and summary collected from Hindi News Websites.
- [Hindi Text Short Summarization Corpus](https://www.kaggle.com/disisbig/hindi-text-short-summarization-corpus) is a collection of ~330k articles with their headlines collected from Hindi News Websites.
- [Old Newspapers Hindi](https://www.kaggle.com/crazydiv/oldnewspapershindi) is a cleaned subset of HC Corpora newspapers.

## Training procedure
### Preprocessing

The texts are tokenized using a byte version of Byte-Pair Encoding (BPE) and a vocabulary size of 50265. The inputs of
the model take pieces of 512 contiguous token that may span over documents. The beginning of a new document is marked
with `<s>` and the end of one by `</s>`. 
- We had to perform cleanup of **mC4** and **oscar** datasets by removing all non hindi (non Devanagari) characters from the datasets. 
- We tried to filter out evaluation set of WikiNER of [IndicGlue](https://indicnlp.ai4bharat.org/indic-glue/) benchmark by [manual labelling](https://github.com/amankhandelia/roberta_hindi/blob/master/wikiner_incorrect_eval_set.csv)  where the actual labels were not correct and modifying the [downstream evaluation dataset](https://github.com/amankhandelia/roberta_hindi/blob/master/utils.py). 


The details of the masking procedure for each sentence are the following:
- 15% of the tokens are masked.
- In 80% of the cases, the masked tokens are replaced by `<mask>`.
- In 10% of the cases, the masked tokens are replaced by a random token (different) from the one they replace.
- In the 10% remaining cases, the masked tokens are left as is.
Contrary to BERT, the masking is done dynamically during pretraining (e.g., it changes at each epoch and is not fixed).

### Pretraining
The model was trained on Google Cloud Engine TPUv3-8 machine (with 335 GB of RAM, 1000 GB of hard drive, 96 CPU cores).A randomized shuffle of combined dataset of **mC4, oscar** and other datasets listed above was used to train the model. Training logs are present in [wandb](https://wandb.ai/wandb/hf-flax-roberta-hindi).

## Evaluation Results

RoBERTa Hindi is evaluated on various downstream tasks. The results are summarized below.

| Task                    | Task Type            | IndicBERT | HindiBERTa | Indic Transformers Hindi BERT | RoBERTa Hindi Guj San | RoBERTa Hindi |
|-------------------------|----------------------|-----------|------------|-------------------------------|-----------------------|---------------|
| BBC News Classification | Genre Classification | **76.44**     | 66.86      | **77.6**                          | 64.9                  | 73.67         |
| WikiNER                 | Token Classification | -         | 90.68      | **95.09**                         | 89.61                 | **92.76**         |
| IITP Product Reviews    | Sentiment Analysis   | **78.01**     | 73.23      | **78.39**                         | 66.16                 | 75.53         |
| IITP Movie Reviews      | Sentiment Analysis   | 60.97     | 52.26      | **70.65**                         | 49.35                 | **61.29**         |

## Team Members
- Aman K ([amankhandelia](https://huggingface.co/amankhandelia))
- Haswanth Aekula ([hassiahk](https://huggingface.co/hassiahk))
- Kartik Godawat ([dk-crazydiv](https://huggingface.co/dk-crazydiv))
- Prateek Agrawal ([prateekagrawal](https://huggingface.co/prateekagrawal))
- Rahul Dev ([mlkorra](https://huggingface.co/mlkorra))


## Credits
Huge thanks to Hugging Face 🤗 & Google Jax/Flax team for such a wonderful community week, especially for providing such massive computing resources. Big thanks to [Suraj Patil](https://huggingface.co/valhalla) & [Patrick von Platen](https://huggingface.co/patrickvonplaten) for mentoring during the whole week.

<img src=https://pbs.twimg.com/media/E443fPjX0AY1BsR.jpg:medium>