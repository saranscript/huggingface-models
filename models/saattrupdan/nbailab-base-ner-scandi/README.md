---
language:
- da
- no
- nb
- nn
- sv
- fo
- is
license: mit
datasets:
- dane
- norne
- wikiann
- suc3.0
model-index:
- name: nbailab-base-ner-scandi
  results: []
widget:
- "Hans er en professor på Københavns Universitetet i København, og han er en rigtig københavner. Hans kat, altså Hans' kat, Lisa, er supersød. Han fik købt en Mona Lisa på tilbud i Netto og gav den til sin kat, og nu er Mona Lisa'en Lisa's kæreste eje. Hans bror Peter og Hans besluttede, at Peterskirken skulle have fint besøg. Men nu har de begge Corona."
inference:
  parameters:
    aggregation_strategy: "first"
---

# ScandiNER - Named Entity Recognition model for Scandinavian Languages

This model is a fine-tuned version of [NbAiLab/nb-bert-base](https://huggingface.co/NbAiLab/nb-bert-base) for Named Entity Recognition for Danish, Norwegian (both Bokmål and Nynorsk), Swedish, Icelandic and Faroese. It has been fine-tuned on the concatenation of [DaNE](https://aclanthology.org/2020.lrec-1.565/), [NorNE](https://arxiv.org/abs/1911.12146), [SUC 3.0](https://spraakbanken.gu.se/en/resources/suc3) and the Icelandic and Faroese parts of the [WikiANN](https://aclanthology.org/P17-1178/) dataset. It also works reasonably well on English sentences, given the fact that the pretrained model is also trained on English data along with Scandinavian languages.

The model will predict the following four entities:

| **Tag** | **Name** | **Description** |
| :------ | :------- | :-------------- |
| `PER` | Person | The name of a person (e.g., *Birgitte* and *Mohammed*) |
| `LOC` | Location | The name of a location (e.g., *Tyskland* and *Djurgården*) |
| `ORG` | Organisation | The name of an organisation (e.g., *Bunnpris* and *Landsbankinn*) |
| `MISC` | Miscellaneous | A named entity of a different kind (e.g., *Ūjķnustu pund* and *Mona Lisa*) |


## Quick start

You can use this model in your scripts as follows:

```python
>>> from transformers import pipeline
>>> import pandas as pd
>>> ner = pipeline(task='ner', 
...                model='saattrupdan/nbailab-base-ner-scandi', 
...                aggregation_strategy='first')
>>> result = ner('Borghild kjøper seg inn i Bunnpris')
>>> pd.DataFrame.from_records(result)
  entity_group     score      word  start  end
0          PER  0.981257  Borghild      0    8
1          ORG  0.974099  Bunnpris     26   34
```


## Performance

The following is the Micro-F1 NER performance on Scandinavian NER test datasets, compared with the current state-of-the-art. The models have been evaluated on the test set along with 9 bootstrapped versions of it, with the mean and 95% confidence interval shown here:

| **Model ID** | **DaNE** | **NorNE-NB** | **NorNE-NN** | **SUC 3.0** | **WikiANN-IS** | **WikiANN-FO** | **Average** |
| :----------- | -------: | -----------: | -----------: | ----------: | -------------: | -------------: | ----------: |
| saattrupdan/nbailab-base-ner-scandi | **87.44 ± 0.81** | **91.06 ± 0.26** | **90.42 ± 0.61** | **88.37 ± 0.17** | **88.61 ± 0.41** | **90.22 ± 0.46** | **89.08 ± 0.46** |
| chcaa/da\_dacy\_large\_trf | 83.61 ± 1.18 | 78.90 ± 0.49 | 72.62 ± 0.58 | 53.35 ± 0.17 | 50.57 ± 0.46 | 51.72 ± 0.52 | 63.00 ± 0.57 |
| RecordedFuture/Swedish-NER | 64.09 ± 0.97 | 61.74 ± 0.50 | 56.67 ± 0.79 | 66.60 ± 0.27 | 34.54 ± 0.73 | 42.16 ± 0.83 | 53.32 ± 0.69 |
| Maltehb/danish-bert-botxo-ner-dane | 69.25 ± 1.17 | 60.57 ± 0.27 | 35.60 ± 1.19 | 38.37 ± 0.26 | 21.00 ± 0.57 | 27.88 ± 0.48 | 40.92 ± 0.64 |
| Maltehb/-l-ctra-danish-electra-small-uncased-ner-dane | 70.41 ± 1.19 | 48.76 ± 0.70 | 27.58 ± 0.61 | 35.39 ± 0.38 | 26.22 ± 0.52 | 28.30 ± 0.29 | 39.70 ± 0.61 |
| radbrt/nb\_nocy\_trf | 56.82 ± 1.63 | 68.20 ± 0.75 | 69.22 ± 1.04 | 31.63 ± 0.29 | 20.32 ± 0.45 | 12.91 ± 0.50 | 38.08 ± 0.75 | 

Aside from its high accuracy, it's also substantially **smaller** and **faster** than the previous state-of-the-art:

| **Model ID** | **Samples/second** | **Model size** |
| :----------- | -----------------: | -------------: |
| saattrupdan/nbailab-base-ner-scandi | 4.16 ± 0.18 | 676 MB |
| chcaa/da\_dacy\_large\_trf | 0.65 ± 0.01 | 2,090 MB |


## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 90135.90000000001
- num_epochs: 1000

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Micro F1 | Micro F1 No Misc |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|:----------------:|
| 0.6682        | 1.0   | 2816  | 0.0872          | 0.6916   | 0.7306           |
| 0.0684        | 2.0   | 5632  | 0.0464          | 0.8167   | 0.8538           |
| 0.0444        | 3.0   | 8448  | 0.0367          | 0.8485   | 0.8783           |
| 0.0349        | 4.0   | 11264 | 0.0316          | 0.8684   | 0.8920           |
| 0.0282        | 5.0   | 14080 | 0.0290          | 0.8820   | 0.9033           |
| 0.0231        | 6.0   | 16896 | 0.0283          | 0.8854   | 0.9060           |
| 0.0189        | 7.0   | 19712 | 0.0253          | 0.8964   | 0.9156           |
| 0.0155        | 8.0   | 22528 | 0.0260          | 0.9016   | 0.9201           |
| 0.0123        | 9.0   | 25344 | 0.0266          | 0.9059   | 0.9233           |
| 0.0098        | 10.0  | 28160 | 0.0280          | 0.9091   | 0.9279           |
| 0.008         | 11.0  | 30976 | 0.0309          | 0.9093   | 0.9287           |
| 0.0065        | 12.0  | 33792 | 0.0313          | 0.9103   | 0.9284           |
| 0.0053        | 13.0  | 36608 | 0.0322          | 0.9078   | 0.9257           |
| 0.0046        | 14.0  | 39424 | 0.0343          | 0.9075   | 0.9256           |


### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
