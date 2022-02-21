---
language:
- en
tags:
- ner
- ncbi
- disease
- pubmed
- bioinfomatics
license: apache-2.0
datasets:
- ncbi-disease
- bc5cdr
widget:
- text: "Hepatocyte nuclear factor 4 alpha (HNF4α) is regulated by different promoters to generate two isoforms, one of which functions as a tumor suppressor. Here, the authors reveal that induction of the alternative isoform in hepatocellular carcinoma inhibits the circadian clock by repressing BMAL1, and the reintroduction of BMAL1 prevents HCC tumor growth."

---

# NER to find Gene & Gene products
> The model was trained on ncbi-disease, BC5CDR dataset, pretrained on this [pubmed-pretrained roberta model](/raynardj/roberta-pubmed)
All the labels, the possible token classes.
```json
{"label2id": {
    "O": 0,
    "Disease":1,
  }
 }
```
 
Notice, we removed the 'B-','I-' etc from data label.🗡
 
## This is the template we suggest for using the model
```python
from transformers import pipeline
PRETRAINED = "raynardj/ner-disease-ncbi-bionlp-bc5cdr-pubmed"
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