---
language:
- en
tags:
- ner
- gene
- protein
- rna
- bioinfomatics
license: apache-2.0
datasets:
- jnlpba
widget:
- text: "It consists of 25 exons encoding a 1,278-amino acid glycoprotein that is composed of 13 transmembrane domains"
---

# NER to find Gene & Gene products
> The model was trained on jnlpba dataset, pretrained on this [pubmed-pretrained roberta model](/raynardj/roberta-pubmed)

All the labels, the possible token classes.
```json
{"label2id": {
    "DNA": 2,
    "O": 0,
    "RNA": 5,
    "cell_line": 4,
    "cell_type": 3,
    "protein": 1
  }
 }
```
 
Notice, we removed the 'B-','I-' etc from data label.🗡
 
## This is the template we suggest for using the model
```python
from transformers import pipeline

PRETRAINED = "raynardj/ner-gene-dna-rna-jnlpba-pubmed"
ner = pipeline(task="ner",model=PRETRAINED, tokenizer=PRETRAINED)
ner("Your text", aggregation_strategy="first")
```
And here is to make your output more consecutive ⭐️

```python
import pandas as pd
from transformers import AutoTokenizer
tokenizer = AutoTokenizer.from_pretrained(PRETRAINED)

def clean_output(outputs):
    results = []
    current = []
    last_idx = 0
    # make to sub group by position
    for output in outputs:
        if output["index"]-1==last_idx:
            current.append(output)
        else:
            results.append(current)
            current = [output, ]
        last_idx = output["index"]
    if len(current)>0:
        results.append(current)
    
    # from tokens to string
    strings = []
    for c in results:
        tokens = []
        starts = []
        ends = []
        for o in c:
            tokens.append(o['word'])
            starts.append(o['start'])
            ends.append(o['end'])

        new_str = tokenizer.convert_tokens_to_string(tokens)
        if new_str!='':
            strings.append(dict(
                word=new_str,
                start = min(starts),
                end = max(ends),
                entity = c[0]['entity']
            ))
    return strings

def entity_table(pipeline, **pipeline_kw):
    if "aggregation_strategy" not in pipeline_kw:
        pipeline_kw["aggregation_strategy"] = "first"
    def create_table(text):
        return pd.DataFrame(
            clean_output(
                pipeline(text, **pipeline_kw)
            )
        )
    return create_table

# will return a dataframe
entity_table(ner)(YOUR_VERY_CONTENTFUL_TEXT)
```

> check our NER model on
* [gene and gene products](/raynardj/ner-gene-dna-rna-jnlpba-pubmed)
* [chemical substance](/raynardj/ner-chemical-bionlp-bc5cdr-pubmed).
* [disease](/raynardj/ner-disease-ncbi-bionlp-bc5cdr-pubmed)