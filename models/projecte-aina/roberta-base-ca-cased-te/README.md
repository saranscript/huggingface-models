---

language:

- ca

license: ???

tags:

- "catalan"

- "textual entailment"

- "teca"

- "CaText"

- "Catalan Textual Corpus"

datasets:

- "projecte-aina/teca"  

metrics:

- "accuracy"


model-index:
- name: roberta-base-ca-cased-te
  results:
  - task: 
      type: text-classification  # Required. Example: automatic-speech-recognition
    dataset:
      type:   projecte-aina/teca
      name: teca
    metrics:
      - type: accuracy
        value: 0.7912139892578125
        
widget:

- text: "M'agrades. T'estimo." 

- text: "M'agrada el sol i la calor. A la Garrotxa plou molt."

- text: "El llibre va caure per la finestra. El llibre va sortir volant."

- text: "El meu aniversari és el 23 de maig. Faré anys a finals de maig."

---

# Catalan BERTa (RoBERTa-base) finetuned for Textual Entailment.

The **roberta-base-ca-cased-te** is a Textual Entailment (TE) model for the Catalan language fine-tuned from the [BERTa](https://huggingface.co/PlanTL-GOB-ES/roberta-base-ca) model, a [RoBERTa](https://arxiv.org/abs/1907.11692) base model pre-trained on a medium-size corpus collected from publicly available corpora and crawlers (check the BERTa model card for more details).

## Datasets
We used the TE dataset in Catalan called [TECA](https://huggingface.co/datasets/projecte-aina/viquiquad) for training and evaluation.

## Evaluation and results
We evaluated the roberta-base-ca-cased-te on the TECA test set against standard multilingual and monolingual baselines:

| Model        | TECA (accuracy) | 
| ------------|:----|
| BERTa       | 79.12 |
| mBERT       | 74.78 |
| XLM-RoBERTa | 75.44 |
| WikiBERT-ca | x |

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
