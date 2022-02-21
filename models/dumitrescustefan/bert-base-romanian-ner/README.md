---
language: ro
datasets:
- ronec
license: mit
---
# bert-base-romanian-ner

Updated: 21.01.2022

## Model description

**bert-base-romanian-ner** is a fine-tuned BERT model that is ready to use for **Named Entity Recognition** and achieves **state-of-the-art performance** for the NER task. It has been trained to recognize **15** types of entities: persons, geo-political entities, locations, organizations, languages, national_religious_political entities, datetime, period, quantity, money, numeric, ordinal, facilities, works of art and events.

Specifically, this model is a [bert-base-romanian-cased-v1](https://huggingface.co/dumitrescustefan/bert-base-romanian-cased-v1) model that was fine-tuned on [RONEC version 2.0](https://github.com/dumitrescustefan/ronec), which holds 12330 sentences with over 0.5M tokens, to a total of 80.283 distinctly annotated entities. RONECv2 is a BIO2 annotated corpus, meaning this model will generate "B-" and "I-" style labels for entities.  

The model will generate labels according to the following list: ['O', 'B-PERSON', 'I-PERSON', 'B-ORG', 'I-ORG', 'B-GPE', 'I-GPE', 'B-LOC', 'I-LOC', 'B-NAT_REL_POL', 'I-NAT_REL_POL', 'B-EVENT', 'I-EVENT', 'B-LANGUAGE', 'I-LANGUAGE', 'B-WORK_OF_ART', 'I-WORK_OF_ART', 'B-DATETIME', 'I-DATETIME', 'B-PERIOD', 'I-PERIOD', 'B-MONEY', 'I-MONEY', 'B-QUANTITY', 'I-QUANTITY', 'B-NUMERIC', 'I-NUMERIC', 'B-ORDINAL', 'I-ORDINAL', 'B-FACILITY', 'I-FACILITY']. Label 'O' represents Other. 

### How to use

There are 2 ways to use this model: 

#### Directly in Transformers:

You can use this model with Transformers *pipeline* for NER; you will have to handle word tokenization in multiple subtokens cases with different labels.

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline
tokenizer = AutoTokenizer.from_pretrained("dumitrescustefan/bert-base-romanian-ner")
model = AutoModelForTokenClassification.from_pretrained("dumitrescustefan/bert-base-romanian-ner")
nlp = pipeline("ner", model=model, tokenizer=tokenizer)
example = "Alex cumpără un bilet pentru trenul 3118 în direcția Cluj cu plecare la ora 13:00."
ner_results = nlp(example)
print(ner_results)
```

#### Use in a Python package

``pip install roner``

Easy, takes care of word-token alignment, long sequences, etc. See details at [https://github.com/dumitrescustefan/roner](https://github.com/dumitrescustefan/roner)


#### Don't forget!

Remember to always sanitize your text! Replace _s_ and _t_ cedilla-letters to comma-letters **before processing your text** with these models, with :

```
text = text.replace("ţ", "ț").replace("ş", "ș").replace("Ţ", "Ț").replace("Ş", "Ș")
```

## NER evaluation results

```
 'test/ent_type': 0.9276865720748901,
 'test/exact': 0.9118986129760742,
 'test/partial': 0.9356381297111511,
 'test/strict': 0.8921924233436584
```

## Corpus details

The corpus has the following classes and distribution in the train/valid/test splits:

| Classes      	| Total  	    | Train  	|         	| Valid  	|         	| Test   	|         	|
|-------------	|:------:	    |:------:	|:-------:	|:------:	|:-------:	|:------:	|:-------:	|
|            	| #     	    | #     	| %     	| # 	    | % 	    | #     	| %     	|
| PERSON      	|  **26130** 	| 19167  	|  73.35  	|  2733  	|  10.46  	|  4230  	|  16.19  	|
| GPE         	|  **11103** 	|  8193  	|  73.79  	|  1182  	|  10.65  	|  1728  	|   15.56 	|
| LOC         	|  **2467**  	|  1824  	|  73.94  	|  270   	|  10.94  	|  373   	|  15.12  	|
| ORG         	|  **7880**  	|  5688  	|  72.18  	|   880  	|  11.17  	|  1312  	|  16.65  	|
| LANGUAGE    	|   **467**  	|   342  	|  73.23  	|   52   	|  11.13  	|   73   	|  15.63  	|
| NAT_REL_POL 	|  **4970**  	|  3673  	|  73.90  	|   516  	|  10.38  	|   781  	|  15.71  	|
| DATETIME    	|  **9614**  	|  6960  	|  72.39  	|  1029  	|   10.7  	|  1625  	|   16.9  	|
| PERIOD      	|  **1188**  	|   862  	|  72.56  	|   129  	|  10.86  	|   197  	|  16.58  	|
| QUANTITY    	|  **1588**  	|  1161  	|  73.11  	|   181  	|   11.4  	|   246  	|  15.49  	|
| MONEY       	|  **1424**  	|  1041  	|  73.10  	|   159  	|  11.17  	|   224  	|  15.73  	|
| NUMERIC     	|  **7735**  	|  5734  	|  74.13  	|   814  	|  10.52  	|  1187  	|  15.35  	|
| ORDINAL     	|  **1893**  	|  1377  	|   72.74 	|   212  	|   11.2  	|   304  	|  16.06  	|
| FACILITY    	|  **1126**  	|   840  	|   74.6  	|   113  	|  10.04  	|   173  	|  15.36  	|
| WORK_OF_ART 	|  **1596**  	|  1157  	|  72.49  	|   176  	|  11.03  	|   263  	|  16.48  	|
| EVENT       	|  **1102**  	|   826  	|  74.95  	|   107  	|   9.71  	|   169  	|  15.34  	|


### BibTeX entry and citation info

Please consider citing the following [paper](https://arxiv.org/abs/1909.01247) as a thank you to the authors of the RONEC, even if it describes v1 of the corpus and you are using a model trained on v2: 
```
Dumitrescu, Stefan Daniel, and Andrei-Marius Avram. "Introducing RONEC--the Romanian Named Entity Corpus." arXiv preprint arXiv:1909.01247 (2019).
```
or in .bibtex format:
```
@article{dumitrescu2019introducing,
  title={Introducing RONEC--the Romanian Named Entity Corpus},
  author={Dumitrescu, Stefan Daniel and Avram, Andrei-Marius},
  journal={arXiv preprint arXiv:1909.01247},
  year={2019}
}
```
