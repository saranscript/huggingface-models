
---
language: 
  - en
license: "apache-2.0"
datasets:
- CoNLL-2003
metrics:
- F1

---

This is a T5 small model finetuned on CoNLL-2003 dataset for named entity recognition (NER).

Example Input and Output:
“Recognize all the named entities in this sequence (replace named entities with one of [PER], [ORG], [LOC], [MISC]): When Alice visited New York” → “When PER visited LOC LOC"

Evaluation Result:

% of match (for comparison with ExT5: https://arxiv.org/pdf/2111.10952.pdf): 

| Model| ExT5_{Base} | This Model | T5_NER_CONLL_OUTPUTLIST 
| :---: | :---: | :---: | :---: |
| % of Complete Match| 86.53 | 79.03 | TBA| 



There are some outputs (212/3453 or 6.14% that does not have the same length as the input)

F1 score on testing set of those with matching length :

| Model | This Model | T5_NER_CONLL_OUTPUTLIST | BERTbase 
| :---: | :---: | :---: | :---: |
| F1| 0.8901 | 0.8691| 0.9240

**Caveat: The testing set of these aren't the same, due to matching length issue... 
T5_NER_CONLL_OUTPUTLIST only has 27/3453 missing length (only 0.78%); The BERT number is directly from their paper (https://arxiv.org/pdf/1810.04805.pdf)




