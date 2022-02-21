---
language: 
- el
- en

tags:
- xlm-roberta-base
datasets:
- multi_nli
- snli
- allnli_greek

metrics:
- accuracy
pipeline_tag: zero-shot-classification
widget:
- text: "Η Facebook κυκλοφόρησε τα πρώτα «έξυπνα» γυαλιά επαυξημένης πραγματικότητας."
  candidate_labels: "τεχνολογία, πολιτική, αθλητισμός"
  multi_class: false
license: apache-2.0
---

# Cross-Encoder for Greek Natural Language Inference (Textual Entailment) & Zero-Shot Classification 
## By the Hellenic Army Academy (SSE) and the Technical University of Crete (TUC)

This model was trained using [SentenceTransformers](https://sbert.net) [Cross-Encoder](https://www.sbert.net/examples/applications/cross-encoder/README.html) class.

## Training Data
The model was trained on the the combined Greek+English version of the AllNLI dataset(sum of [SNLI](https://nlp.stanford.edu/projects/snli/) and [MultiNLI](https://cims.nyu.edu/~sbowman/multinli/)). The Greek part was created using the EN2EL NMT model available [here](https://huggingface.co/lighteternal/SSE-TUC-mt-en-el-cased).

The model can be used in two ways:
* NLI/Textual Entailment: For a given sentence pair, it will output three scores corresponding to the labels: contradiction, entailment, neutral.
* Zero-shot classification through the Huggingface pipeline: Given a sentence and a set of labels/topics, it will output the likelihood of the sentence belonging to each of the topic. Under the hood, the logit for entailment between the sentence and each label is taken as the logit for the candidate label being valid.

## Performance

Evaluation on classification accuracy (entailment, contradiction, neutral) on mixed (Greek+English) AllNLI-dev set:

| Metric | Value |
| --- | --- |
| Accuracy | 0.8409 |



## To use the model for NLI/Textual Entailment

#### Usage with sentence_transformers

Pre-trained models can be used like this:
```python
from sentence_transformers import CrossEncoder
model = CrossEncoder('lighteternal/nli-xlm-r-greek')
scores = model.predict([('Δύο άνθρωποι συναντιούνται στο δρόμο', 'Ο δρόμος έχει κόσμο'),
                        ('Ένα μαύρο αυτοκίνητο ξεκινάει στη μέση του πλήθους.', 'Ένας άντρας οδηγάει σε ένα μοναχικό δρόμο'), 
                        ('Δυο γυναίκες μιλάνε στο κινητό', 'Το τραπέζι ήταν πράσινο')])


#Convert scores to labels
label_mapping = ['contradiction', 'entailment', 'neutral']
labels = [label_mapping[score_max] for score_max in scores.argmax(axis=1)]
print(scores, labels)

# Οutputs
#[[-3.1526504  2.9981945 -0.3108107]
# [ 5.0549307 -2.757949  -1.6220676]
# [-0.5124733 -2.2671669  3.1630592]] ['entailment', 'contradiction', 'neutral']
 ```
 
#### Usage with Transformers AutoModel
You can use the model also directly with Transformers library (without SentenceTransformers library):
```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch

model = AutoModelForSequenceClassification.from_pretrained('lighteternal/nli-xlm-r-greek')
tokenizer = AutoTokenizer.from_pretrained('lighteternal/nli-xlm-r-greek')

features = tokenizer(['Δύο άνθρωποι συναντιούνται στο δρόμο', 'Ο δρόμος έχει κόσμο'], 
                    ['Ένα μαύρο αυτοκίνητο ξεκινάει στη μέση του πλήθους.', 'Ένας άντρας οδηγάει σε ένα μοναχικό δρόμο.'],  
                    padding=True, truncation=True, return_tensors="pt")

model.eval()
with torch.no_grad():
    scores = model(**features).logits
    label_mapping = ['contradiction', 'entailment', 'neutral']
    labels = [label_mapping[score_max] for score_max in scores.argmax(dim=1)]
    print(labels)
```

## To use the model for Zero-Shot Classification
This model can also be used for zero-shot-classification:
```python
from transformers import pipeline

classifier = pipeline("zero-shot-classification", model='lighteternal/nli-xlm-r-greek')

sent = "Το Facebook κυκλοφόρησε τα πρώτα «έξυπνα» γυαλιά επαυξημένης πραγματικότητας"
candidate_labels = ["πολιτική", "τεχνολογία", "αθλητισμός"]
res = classifier(sent, candidate_labels)
print(res)

#outputs:
#{'sequence': 'Το Facebook κυκλοφόρησε τα πρώτα «έξυπνα» γυαλιά επαυξημένης πραγματικότητας', 'labels': ['τεχνολογία', 'αθλητισμός', 'πολιτική'], 'scores': [0.8380699157714844, 0.09086982160806656, 0.07106029987335205]}
``` 
### Acknowledgement
The research work was supported by the Hellenic Foundation for Research and Innovation (HFRI) under the HFRI PhD Fellowship grant (Fellowship Number:50, 2nd call)

### Citation info
Citation for the Greek model TBA.
Based on the work [Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks](https://arxiv.org/abs/1908.10084)
Kudos to @nreimers (Nils Reimers) for his support on Github . 
