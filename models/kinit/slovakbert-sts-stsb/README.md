---
language: 
- sk
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- sts
license: cc
datasets:
- glue
metrics:
- spearmanr
widget:
 source_sentence: "Izrael uskutočnil letecké údery v blízkosti Damasku."
 sentences:
  - "Izrael uskutočnil vzdušný útok na Sýriu."
  - "Pes leží na gauči a má hlavu na bielom vankúši."
---


# Sentence similarity model based on SlovakBERT

This is a sentence similarity model based on [SlovakBERT](https://huggingface.co/gerulata/slovakbert). The model was fine-tuned using [STSbenchmark](ixa2.si.ehu.eus/stswiki/index.php/STSbenchmark) [Cer et al 2017] translated to Slovak using [M2M100](https://huggingface.co/facebook/m2m100_1.2B). The model can be used as an universal sentence encoder for Slovak sentences.

## Results

The model was evaluated in [our paper](https://arxiv.org/abs/2109.15254) [Pikuliak et al 2021, Section 4.3]. It achieves \\(0.791\\) Spearman correlation on STSbenchmark test set.


## Usage

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["This is an example sentence", "Each sentence is converted"]

model = SentenceTransformer('kinit/slovakbert-sts-stsb')
embeddings = model.encode(sentences)
print(embeddings)
```


## Cite

```
@article{DBLP:journals/corr/abs-2109-15254,
  author    = {Mat{\'{u}}s Pikuliak and
               Stefan Grivalsky and
               Martin Konopka and
               Miroslav Blst{\'{a}}k and
               Martin Tamajka and
               Viktor Bachrat{\'{y}} and
               Mari{\'{a}}n Simko and
               Pavol Bal{\'{a}}zik and
               Michal Trnka and
               Filip Uhl{\'{a}}rik},
  title     = {SlovakBERT: Slovak Masked Language Model},
  journal   = {CoRR},
  volume    = {abs/2109.15254},
  year      = {2021},
  url       = {https://arxiv.org/abs/2109.15254},
  eprinttype = {arXiv},
  eprint    = {2109.15254},
}
```
