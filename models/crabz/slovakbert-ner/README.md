---
license: mit
language:
- sk
tags:
- generated_from_trainer
datasets:
- wikiann
metrics:
- precision
- recall
- f1
- accuracy
inference: false
widget:
- text: "Zuzana Čaputová sa narodila 21. júna 1973 v Bratislave."
  example_title: "Named Entity Recognition"
model-index:
- name: slovakbert-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann
      type: wikiann
      args: sk
    metrics:
    - name: Precision
      type: precision
      value: 0.9327115256495669
    - name: Recall
      type: recall
      value: 0.9470124013528749
    - name: F1
      type: f1
      value: 0.9398075632132469
    - name: Accuracy
      type: accuracy
      value: 0.9785228256835333
---

# Named Entity Recognition based on SlovakBERT

This model is a fine-tuned version of [gerulata/slovakbert](https://huggingface.co/gerulata/slovakbert) on the Slovak wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1600
- Precision: 0.9327
- Recall: 0.9470
- F1: 0.9398
- Accuracy: 0.9785

## Intended uses & limitations

Supported classes: LOCATION, PERSON, ORGANIZATION

```
from transformers import pipeline


ner_pipeline = pipeline(task='ner', model='crabz/slovakbert-ner')
input_sentence = "Minister financií a líder mandátovo najsilnejšieho hnutia OĽaNO Igor Matovič upozorňuje, že následky tretej vlny budú na Slovensku veľmi veľké."
classifications = ner_pipeline(input_sentence)
``` 

with `displaCy`:

```
import spacy
from spacy import displacy


ner_map = {0: '0', 1: 'B-OSOBA', 2: 'I-OSOBA', 3: 'B-ORGANIZÁCIA', 4: 'I-ORGANIZÁCIA', 5: 'B-LOKALITA', 6: 'I-LOKALITA'}

entities = []
for i in range(len(classifications)):
    if classifications[i]['entity'] != 0:
        if ner_map[classifications[i]['entity']][0] == 'B':
            j = i + 1
            while j < len(classifications) and ner_map[classifications[j]['entity']][0] == 'I':
                j += 1
            entities.append((ner_map[classifications[i]['entity']].split('-')[1], classifications[i]['start'],
                             classifications[j - 1]['end']))

nlp = spacy.blank("en")  # it should work with any language

doc = nlp(input_sentence)

ents = []
for ee in entities:
    ents.append(doc.char_span(ee[1], ee[2], ee[0]))

doc.ents = ents

options = {"ents": ["OSOBA", "ORGANIZÁCIA", "LOKALITA"],
           "colors": {"OSOBA": "lightblue", "ORGANIZÁCIA": "lightcoral", "LOKALITA": "lightgreen"}}
displacy_html = displacy.render(doc, style="ent", options=options)

```

<div class="entities" style="line-height: 2.5; direction: ltr">Minister financií a líder mandátovo najsilnejšieho hnutia
<mark class="entity" style="background: lightcoral; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
    OĽaNO
    <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">ORGANIZÁCIA</span>
</mark>

<mark class="entity" style="background: lightblue; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
    Igor Matovič
    <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">OSOBA</span>
</mark>
 upozorňuje, že následky tretej vlny budú na
<mark class="entity" style="background: lightgreen; padding: 0.45em 0.6em; margin: 0 0.25em; line-height: 1; border-radius: 0.35em;">
    Slovensku
    <span style="font-size: 0.8em; font-weight: bold; line-height: 1; border-radius: 0.35em; vertical-align: middle; margin-left: 0.5rem">LOKALITA</span>
</mark>
 veľmi veľké.</div>

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2342        | 1.0   | 625  | 0.1233          | 0.8891    | 0.9076 | 0.8982 | 0.9667   |
| 0.1114        | 2.0   | 1250 | 0.1079          | 0.9118    | 0.9269 | 0.9193 | 0.9725   |
| 0.0817        | 3.0   | 1875 | 0.1093          | 0.9173    | 0.9315 | 0.9243 | 0.9747   |
| 0.0438        | 4.0   | 2500 | 0.1076          | 0.9188    | 0.9353 | 0.9270 | 0.9743   |
| 0.028         | 5.0   | 3125 | 0.1230          | 0.9143    | 0.9387 | 0.9264 | 0.9744   |
| 0.0256        | 6.0   | 3750 | 0.1204          | 0.9246    | 0.9423 | 0.9334 | 0.9765   |
| 0.018         | 7.0   | 4375 | 0.1332          | 0.9292    | 0.9416 | 0.9353 | 0.9770   |
| 0.0107        | 8.0   | 5000 | 0.1339          | 0.9280    | 0.9427 | 0.9353 | 0.9769   |
| 0.0079        | 9.0   | 5625 | 0.1368          | 0.9326    | 0.9442 | 0.9383 | 0.9785   |
| 0.0065        | 10.0  | 6250 | 0.1490          | 0.9284    | 0.9445 | 0.9364 | 0.9772   |
| 0.0061        | 11.0  | 6875 | 0.1566          | 0.9328    | 0.9433 | 0.9380 | 0.9778   |
| 0.0031        | 12.0  | 7500 | 0.1555          | 0.9339    | 0.9473 | 0.9406 | 0.9787   |
| 0.0024        | 13.0  | 8125 | 0.1548          | 0.9349    | 0.9462 | 0.9405 | 0.9787   |
| 0.0015        | 14.0  | 8750 | 0.1562          | 0.9330    | 0.9469 | 0.9399 | 0.9788   |
| 0.0013        | 15.0  | 9375 | 0.1600          | 0.9327    | 0.9470 | 0.9398 | 0.9785   |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu113
- Datasets 1.15.1
- Tokenizers 0.10.3
