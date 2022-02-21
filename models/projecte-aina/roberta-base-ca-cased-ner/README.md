---

language:

- ca

license: ???

tags:

- "catalan"

- "named entity recognition"

- "ner"

- "CaText"

- "Catalan Textual Corpus"

datasets:

- "projecte-aina/ancora-ca-ner"  

metrics:

- f1

model-index:
- name: roberta-base-ca-cased-te
  results:
  - task: 
      type: token-classification 
    dataset:
      type:   projecte-aina/ancora-ca-ner
      name: ancora-ca-ner
    metrics:
      - type: f1
        value: 0.8963029756537422

widget:

- text: "Em dic Lluïsa i visc a Santa Maria del Camí." 

- text: "L'Aina, la Berta i la Norma són molt amigues."

- text: "El Martí llegeix el Cavall Fort."

---

# Catalan BERTa (RoBERTa-base) finetuned for Named Entity Recognition.

The **roberta-base-ca-cased-ner** is a Named Entity Recognition (NER) model for the Catalan language fine-tuned from the [BERTa](https://huggingface.co/PlanTL-GOB-ES/roberta-base-ca) model, a [RoBERTa](https://arxiv.org/abs/1907.11692) base model pre-trained on a medium-size corpus collected from publicly available corpora and crawlers (check the BERTa model card for more details).

## Datasets
We used the NER dataset in Catalan called [Ancora-ca-ner](https://huggingface.co/datasets/projecte-aina/ancora-ca-ner) for training and evaluation.

## Evaluation and results
We evaluated the _roberta-base-ca-cased-tc_ on the Ancora-ca-ner test set against standard multilingual and monolingual baselines:

| Model        | Ancora-ca-ner (F1)| 
| ------------|:-------------|
| roberta-base-ca-cased-ner | **89.63** |
| mBERT       | 86.38 |
| XLM-RoBERTa | 87.66 | 
| WikiBERT-ca | 77.66 |

For more details, check the fine-tuning and evaluation scripts in the official [GitHub repository](https://github.com/projecte-aina/berta).
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
