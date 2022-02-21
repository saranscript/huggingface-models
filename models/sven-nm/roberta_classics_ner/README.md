---
language: 
  - en
tags:
- classics
- citation mining
widget:
- text: "Homer's Iliad opens with an invocation to the muse (1. 1)."
---

### Model and entities
`roberta_classics_ner` is a domain-specific RoBERTa-based model for named entity recognition in Classical Studies. It recognises bibliographical entities, such as:


| id  | label         | desciption                                  | Example               |
| --- | ------------- | ------------------------------------------- | --------------------- |
| 0   | 'O'           | Out of entity                               |                       | 
| 1   | 'B-AAUTHOR'   | Ancient authors                             | *Herodotus*           |
| 2   | 'I-AAUTHOR'   |                                             |                       |
| 3   | 'B-AWORK'     | The title of an ancient work                | *Symposium*, *Aeneid* |
| 4   | 'I-AWORK'     |                                             |                       |
| 5   | 'B-REFAUWORK' | A structured reference to an ancient work   | *Homer, Il.*          |
| 6   | 'I-REFAUWORK' |                                             |                       |
| 7   | 'B-REFSCOPE'  | The scope of a reference                    | *II.1.993a30–b11*     |
| 8   | 'I-REFSCOPE'  |                                             |                       |
| 9   | 'B-FRAGREF'   | A reference to fragmentary texts or scholia | *Frag. 19. West*      |
| 10  | 'I-FRAGREF'   |                                             |                       |


### Example


```
B-AAUTHOR   B-AWORK                                      B-REFSCOPE
Homer  's   Iliad opens with an invocation to the muse ( 1. 1).
```



### Dataset


`roberta_classics_ner` was fine-tuned and evaluated on `EpiBau`, a dataset which has not been released publicly yet. It is composed of four volumes of [Structures of Epic Poetry](https://www.epische-bauformen.uni-rostock.de/), a compendium on the narrative patterns and structural elements in ancient epic. 
Entity counts of the `Epibau` dataset are the following: 

|                | train-set | dev-set | test-set |
| -------------- | --------- | ------- | -------- |
| word count     | 712462    | 125729  | 122324   |
| AAUTHOR        | 4436      | 1368    | 1511     |
| AWORK          | 3145      | 780     | 670      |
| REFAUWORK      | 5102      | 988     | 1209     |
| REFSCOPE       | 14768     | 3193    | 2847     |
| FRAGREF        | 266       | 29      | 33       |
| total entities | 13822     | 1415    | 2419     |


### Results

The model was developed in the context of experiments reported [here](http://infoscience.epfl.ch/record/291236?&ln=en).Trained and tested on `EpiBau` with a 85-15 split, the model yields a general F1 score of **.82** (micro-averages). Detailed scores are displayed below. Evaluation was performed with the [CLEF-HIPE-scorer](https://github.com/impresso/CLEF-HIPE-2020-scorer), in strict mode) 


| metric    | AAUTHOR | AWORK | REFSCOPE | REFAUWORK |
| --------- | ------- | ----- | -------- | --------- |
| F1        | .819    | .796  | .863     | .756      |
| Precision | .842    | .818  | .860     | .755      |
| Recall    | .797    | .766  | .756     | .866      | 




Questions, remarks, help or contribution ? Get in touch [here](https://github.com/AjaxMultiCommentary), we'll be happy to chat !  

