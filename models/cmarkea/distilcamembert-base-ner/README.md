---
language: fr
license: mit
datasets:
- Jean-Baptiste/wikiner_fr
widget:
- text: "Boulanger, habitant à Boulanger et travaillant dans le magasin Boulanger situé dans la ville de Boulanger. Boulanger a écrit notamment le très célèbre livre intitulé Boulanger édité par la maison d'édition Boulanger."
---
DistilCamemBERT-NER
===================

We present DistilCamemBERT-NER which is [DistilCamemBERT](https://huggingface.co/cmarkea/distilcamembert-base) fine tuned for the NER (Named Entity Recognition) task for the French language. The work is inspired by [Jean-Baptiste/camembert-ner](https://huggingface.co/Jean-Baptiste/camembert-ner) based on the [CamemBERT](https://huggingface.co/camembert-base) model. The problem of the modelizations based on CamemBERT is at the scaling moment, for the production phase for example. Indeed, inference cost can be a technological issue. To counteract this effect, we propose this modelization which **divides the inference time by 2** with the same consumption power thanks to [DistilCamemBERT](https://huggingface.co/cmarkea/distilcamembert-base).

Dataset
-------

The dataset used is [wikiner_fr](https://huggingface.co/datasets/Jean-Baptiste/wikiner_fr) which represents ~170k sentences labelized in 5 categories :
* PER: personality ;
* LOC: location ;
* ORG: organization ;
* MISC: miscellaneous entities (movies title, books, etc.) ;
* O: background (Outside entity).
 
Evaluation results
------------------

| **class**      | **precision (%)** | **recall (%)** | **f1 (%)** | **support (#sub-word)** |
| :------------: | :---------------: | :------------: | :--------: | :---------------------: |
| **global**     | 98.35             | 98.36          | 98.35      | 492'243                 |
| **PER**        | 96.22             | 97.41          | 96.81      | 27'842                  |
| **LOC**        | 93.93             | 93.50          | 93.72      | 31'431                  |
| **ORG**        | 85.13             | 87.08          | 86.10      | 7'662                   |
| **MISC**       | 88.55             | 81.84          | 85.06      | 13'553                  |
| **O**          | 99.40             | 99.55          | 99.47      | 411'755                 |

Benchmark
---------

This model performance is compared to 2 reference models (see below) with the metric [MCC (Matthews Correlation Coefficient)](https://en.wikipedia.org/wiki/Phi_coefficient). The score is given with a factor x100 and the delta gain with DistilCamemBERT-NER used in reference is in parantheses. For the mean inference time measure, an AMD Ryzen 5 4500U @ 2.3GHz with 6 cores was used:

| **model**                                                                                                         | **time (ms)**      | **PER**          | **LOC**          | **ORG**          | **MISC**         | **O**            |
| :---------------------------------------------------------------------------------------------------------------: | :----------------: | :--------------: | :--------------: | :--------------: | :--------------: | :------------- : |
| [cmarkea/distilcamembert-base-ner](https://huggingface.co/cmarkea/distilcamembert-base-ner)                       | **43.44**          | **93.91**        | **88.26**        | **84.03**        | **82.74**        | **91.45**        |
| [Davlan/bert-base-multilingual-cased-ner-hrl](https://huggingface.co/Davlan/bert-base-multilingual-cased-ner-hrl) | 87.56<br/>(+102%)  | 79.93<br/>(-15%) | 70.39<br/>(-22%) | 60.26<br/>(-28%) | n/a<br/>(n/a%)   | 69.95<br/>(-24%) |
| [flair/ner-french](https://huggingface.co/flair/ner-french)                                                       | 314.96<br/>(+625%) | 80.18<br/>(-15%) | 72.11<br/>(-18%) | 67.29<br/>(-20%) | 72.39<br/>(-17%) | 74.34<br/>(-19%) |
<!--- | [Jean-Baptiste/camembert-ner](https://huggingface.co/Jean-Baptiste/camembert-ner)                                 | 83.70<br/>(+93%)   | 95.20<br/>(+1%)  | 90.85<br/>(+3%)  | 89.50<br/>(+6%)  | 89.02<br/>(+8%)  | 92.86<br/>(+2%)  | problème de sur-apprentissage car pas moyen de savoir quelles sont les observations d'éval  --->

How to use DistilCamemBERT-NER
------------------------------

```python
from transformers import pipeline

ner = pipeline(
    task='ner',
    model="cmarkea/distilcamembert-base-ner",
    tokenizer="cmarkea/distilcamembert-base-ner",
    aggregation_strategy="simple"
)
result = ner(
    "Le Crédit Mutuel Arkéa est une banque Française, elle comprend le CMB "
    "qui est une banque située en Bretagne et le CMSO qui est une banque "
    "qui se situe principalement en Aquitaine. C'est sous la présidence de "
    "Louis Lichou, dans les années 1980 que différentes filiales sont créées "
    "au sein du CMB et forment les principales filiales du groupe qui "
    "existent encore aujourd'hui (Federal Finance, Suravenir, Financo, etc.)."
)

result
[{'entity_group': 'ORG',
  'score': 0.99327177,
  'word': 'Crédit Mutuel Arkéa',
  'start': 3,
  'end': 22},
 {'entity_group': 'LOC',
  'score': 0.5869117,
  'word': 'Française',
  'start': 38,
  'end': 47},
 {'entity_group': 'ORG',
  'score': 0.9728106,
  'word': 'CMB',
  'start': 66,
  'end': 69},
 {'entity_group': 'LOC',
  'score': 0.9974824,
  'word': 'Bretagne',
  'start': 99,
  'end': 107},
 {'entity_group': 'ORG',
  'score': 0.956406,
  'word': 'CMSO',
  'start': 114,
  'end': 118},
 {'entity_group': 'LOC',
  'score': 0.99741644,
  'word': 'Aquitaine',
  'start': 169,
  'end': 178},
 {'entity_group': 'PER',
  'score': 0.9988959,
  'word': 'Louis Lichou',
  'start': 208,
  'end': 220},
 {'entity_group': 'ORG',
  'score': 0.93090177,
  'word': 'CMB',
  'start': 291,
  'end': 294},
 {'entity_group': 'ORG',
  'score': 0.9965743,
  'word': 'Federal Finance',
  'start': 374,
  'end': 389},
 {'entity_group': 'ORG',
  'score': 0.99655724,
  'word': 'Suravenir',
  'start': 391,
  'end': 400},
 {'entity_group': 'ORG',
  'score': 0.99653435,
  'word': 'Financo',
  'start': 402,
  'end': 409}]
```