---

language:

- ca

license: ???

tags:

- "catalan"

- "semantic textual similarity"

- "sts-ca"

- "CaText"

- "Catalan Textual Corpus"

datasets:

- "projecte-aina/sts-ca"  

metrics:

- "pearson"


model-index:
- name: roberta-base-ca-cased-sts
  results:
  - task: 
      type: sentence-similarity
    dataset:
      type:   projecte-aina/sts-ca
      name: sts-ca
    metrics:
      - type: pearson
        value: 0.8120486139447483
        
---

# Catalan BERTa (RoBERTa-base) finetuned for Semantic Textual Similarity.

The **roberta-base-ca-cased-sts** is a Semantic Textual Similarity (STS) model for the Catalan language fine-tuned from the [BERTa](https://huggingface.co/PlanTL-GOB-ES/roberta-base-ca) model, a [RoBERTa](https://arxiv.org/abs/1907.11692) base model pre-trained on a medium-size corpus collected from publicly available corpora and crawlers (check the BERTa model card for more details).

## Datasets
We used the STS dataset in Catalan called [STS-ca](https://huggingface.co/datasets/projecte-aina/sts-ca) for training and evaluation.

## Evaluation and results
We evaluated the _roberta-base-ca-cased-sts_ on the STS-ca test set against standard multilingual and monolingual baselines:

| Model       | STS-ca (Pearson)   | 
|:------------|:----|
| roberta-base-ca-cased-sts | **81.20** |
| mBERT       | 76.34 | 
| XLM-RoBERTa | 75.40 |
| WikiBERT-ca | 77.18 | 


For more details, check the fine-tuning and evaluation scripts in the official [GitHub repository](https://github.com/projecte-aina/berta).

## How to use
To get the correct<sup>1</sup> model's prediction scores with values between 0.0 and 5.0, use the following code:

```python
from transformers import pipeline, AutoTokenizer
from scipy.special import logit

model = 'projecte-aina/roberta-base-ca-cased-sts'
tokenizer = AutoTokenizer.from_pretrained(model)
pipe = pipeline('text-classification', model=model, tokenizer=tokenizer)

def prepare(sentence_pairs):
    sentence_pairs_prep = []
    for s1, s2 in sentence_pairs:
        sentence_pairs_prep.append(f"{tokenizer.cls_token} {s1}{tokenizer.sep_token}{tokenizer.sep_token} {s2}{tokenizer.sep_token}")
    return sentence_pairs_prep

sentence_pairs = [("El llibre va caure per la finestra.", "El llibre va sortir volant."),
                  ("M'agrades.", "T'estimo."),
                  ("M'agrada el sol i la calor", "A la Garrotxa plou molt.")]

predictions = pipe(prepare(sentence_pairs), add_special_tokens=False)

# convert back to scores to the original 1 and 5 interval
for prediction in predictions:
    prediction['score'] = logit(prediction['score'])
print(predictions)
```
Expected output:
```
[{'label': 'SIMILARITY', 'score': 2.4280577200108384}, 
{'label': 'SIMILARITY', 'score': 2.132843521240822}, 
{'label': 'SIMILARITY', 'score': 1.615101695426227}]
```

<sup>1</sup> _**avoid using the widget** scores since they are normalized and do not reflect the original annotation values._
## Citing 
If you use any of these resources (datasets or models) in your work, please cite our latest paper:
```bibtex
@inproceedings{armengol-estape-etal-2021-multilingual,
    title = "Are Multilingual Models the Best Choice for Moderately Under-resourced Languages? {A} Comprehensive Assessment for {C}atalan",
    author = "Armengol-Estap{\'e}, Jordi  and
      Carrino, Casimiro Pio  and
      Rodriguez-Penagos, Carlos  and
      de Gibert Bonet, Ona  and
      Armentano-Oller, Carme  and
      Gonzalez-Agirre, Aitor  and
      Melero, Maite  and
      Villegas, Marta",
    booktitle = "Findings of the Association for Computational Linguistics: ACL-IJCNLP 2021",
    month = aug,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.findings-acl.437",
    doi = "10.18653/v1/2021.findings-acl.437",
    pages = "4933--4946",
}
```
