---
language:
- en
tags:
- pytorch
- token-classification
- nominalizations
datasets:
- kleinay/qanom
---

# Nominalization Detector

This model identifies "predicative nominalizations", that is, nominalizations that carry an eventive (or "verbal") meaning in context. It is a `bert-base-cased` pretrained model, fine-tuned for token classification on top of the "nominalization detection" task as defined and annotated by the QANom project [(Klein et. al., COLING 2020)](https://www.aclweb.org/anthology/2020.coling-main.274/).

## Task Description

The model is trained as a binary classifier, classifying candidate nominalizations. 
The candidates are extracted using a POS tagger (filtering common nouns) and additionally lexical resources (e.g. WordNet and CatVar), filtering nouns that have (at least one) derivationally-related verb. In the QANom annotation project, these candidates are given to annotators to decide whether they carry a "verbal" meaning in the context of the sentence. The current model reproduces this binary classification. 

## Demo

Check out our cool [demo](https://huggingface.co/spaces/kleinay/nominalization-detection-demo)!

## Usage

The candidate extraction algorithm is implemented inside the `qanom` package - see the README in the [QANom github repo](https://github.com/kleinay/QANom) for full documentation. The `qanom` package is also available via `pip install qanom`. 

For ease of use, we encapsulated the full nominalization detection pipeline (i.e. candidate extraction + predicate classification) in the `qanom.nominalization_detector.NominalizationDetector` class, which internally utilize this `nominalization-candidate-classifier`:

 ```python
from qanom.nominalization_detector import NominalizationDetector
detector = NominalizationDetector()
 
raw_sentences = ["The construction of the officer 's building finished right after the beginning of the destruction of the previous construction ."]

print(detector(raw_sentences, return_all_candidates=True))
print(detector(raw_sentences, threshold=0.75, return_probability=False))
```   

Outputs:
```json
[[{'predicate_idx': 1,
   'predicate': 'construction',
   'predicate_detector_prediction': True,
   'predicate_detector_probability': 0.7626778483390808,
   'verb_form': 'construct'},
  {'predicate_idx': 4,
   'predicate': 'officer',
   'predicate_detector_prediction': False,
   'predicate_detector_probability': 0.19832570850849152,
   'verb_form': 'officer'},
  {'predicate_idx': 6,
   'predicate': 'building',
   'predicate_detector_prediction': True,
   'predicate_detector_probability': 0.5794129371643066,
   'verb_form': 'build'},
  {'predicate_idx': 11,
   'predicate': 'beginning',
   'predicate_detector_prediction': True,
   'predicate_detector_probability': 0.8937646150588989,
   'verb_form': 'begin'},
  {'predicate_idx': 14,
   'predicate': 'destruction',
   'predicate_detector_prediction': True,
   'predicate_detector_probability': 0.8501205444335938,
   'verb_form': 'destruct'},
  {'predicate_idx': 18,
   'predicate': 'construction',
   'predicate_detector_prediction': True,
   'predicate_detector_probability': 0.7022264003753662,
   'verb_form': 'construct'}]]
```
```json
[[{'predicate_idx': 1, 'predicate': 'construction', 'verb_form': 'construct'},
  {'predicate_idx': 11, 'predicate': 'beginning', 'verb_form': 'begin'},
  {'predicate_idx': 14, 'predicate': 'destruction', 'verb_form': 'destruct'}]]
```
  
## Cite

 ```latex
 @inproceedings{klein2020qanom,
  title={QANom: Question-Answer driven SRL for Nominalizations},
  author={Klein, Ayal and Mamou, Jonathan and Pyatkin, Valentina and Stepanov, Daniela and He, Hangfeng and Roth, Dan and Zettlemoyer, Luke and Dagan, Ido},
  booktitle={Proceedings of the 28th International Conference on Computational Linguistics},
  pages={3069--3083},
  year={2020}
}
 ``` 
