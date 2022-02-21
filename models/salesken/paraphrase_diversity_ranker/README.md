---
tags: salesken
license: apache-2.0
inference: false

---

We have trained a model to evaluate if a paraphrase is a semantic variation to the input query or just a surface level variation. Data augmentation by adding Surface level variations does not add much value to the NLP model training. if the approach to paraphrase generation is "OverGenerate and Rank" , Its important to have a robust model of scoring/ ranking paraphrases. NLG Metrics like bleu ,BleuRT, gleu , Meteor have not proved very effective in scoring paraphrases. 

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification  
import torch
import pandas as pd
import numpy as np
tokenizer = AutoTokenizer.from_pretrained("salesken/paraphrase_diversity_ranker")
model = AutoModelForSequenceClassification.from_pretrained("salesken/paraphrase_diversity_ranker")

input_query = ["tough challenges make you stronger."]
paraphrases =  [
        "tough problems make you stronger",
        "tough problems will make you stronger",
        "tough challenges make you stronger",
        "tough challenges will make you a stronger person",
        "tough challenges will make you stronger",
        "tough tasks make you stronger",
        "the tough task makes you stronger",
        "tough stuff makes you stronger",
        "if tough times make you stronger",
        "the tough part makes you stronger",
        "tough issues strengthens you",
        "tough shit makes you stronger",
        "tough tasks force you to be stronger",
        "tough challenge is making you stronger",
        "tough problems make you have more strength"]
para_pairs=list(pd.MultiIndex.from_product([input_query, paraphrases]))


features = tokenizer(para_pairs,  padding=True, truncation=True, return_tensors="pt")
model.eval()
with torch.no_grad():
    scores = model(**features).logits
    label_mapping = ['surface_level_variation', 'semantic_variation']
    labels = [label_mapping[score_max] for score_max in scores.argmax(dim=1)]

sorted_diverse_paraphrases= np.array(para_pairs)[scores[:,1].sort(descending=True).indices].tolist()
print(sorted_diverse_paraphrases)


# to identify the type of paraphrase (surface-level variation or semantic variation) 
print("Paraphrase type detection=====", list(zip(para_pairs, labels)))
```

============================================================================

For more robust results, filter out the paraphrases which are not semantically 
similar using a model trained on NLI, STS task and then apply the ranker .

```python
from transformers import AutoTokenizer, AutoModelWithLMHead
from transformers import AutoModelForSequenceClassification
from sentence_transformers import SentenceTransformer, util
import torch
import pandas as pd
import numpy as np

tokenizer = AutoTokenizer.from_pretrained("salesken/paraphrase_diversity_ranker")
model = AutoModelForSequenceClassification.from_pretrained("salesken/paraphrase_diversity_ranker")
embedder = SentenceTransformer('stsb-bert-large')

input_query = ["tough challenges make you stronger."]
paraphrases =  [
        "tough problems make you stronger",
        "tough problems will make you stronger",
        "tough challenges make you stronger",
        "tough challenges will make you a stronger person",
        "tough challenges will make you stronger",
        "tough tasks make you stronger",
        "the tough task makes you stronger",
        "tough stuff makes you stronger",
        "tough people make you stronger",
        "if tough times make you stronger",
        "the tough part makes you stronger",
        "tough issues strengthens you",
        "tough shit makes you stronger",
        "tough tasks force you to be stronger",
        "tough challenge is making you stronger",
        "tough problems make you have more strength"]


corpus_embeddings = embedder.encode(paraphrases, convert_to_tensor=True)
query_embedding = embedder.encode(input_query, convert_to_tensor=True)
cos_scores = util.pytorch_cos_sim(query_embedding, corpus_embeddings)[0]
para_set=np.array(paraphrases)
a=cos_scores.sort(descending=True)
para= para_set[a.indices[a.values>=0.7].cpu()].tolist()


para_pairs=list(pd.MultiIndex.from_product([input_query, para]))

import torch
features = tokenizer(para_pairs,  padding=True, truncation=True, return_tensors="pt")
model.eval()
with torch.no_grad():
    scores = model(**features).logits
    label_mapping = ['surface_level_variation', 'semantic_variation']
    labels = [label_mapping[score_max] for score_max in scores.argmax(dim=1)]

sorted_diverse_paraphrases= np.array(para)[scores[:,1].sort(descending=True).indices].tolist()
print("Paraphrases sorted by diversity:=======",sorted_diverse_paraphrases)

# to identify the type of paraphrase (surface-level variation or semantic variation) 
print("Paraphrase type detection=====", list(zip(para_pairs, labels)))

```