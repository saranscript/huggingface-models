---

language:

- ca

license: ???

tags:

- "catalan"

- "text classification"

- "tecla"

- "CaText"

- "Catalan Textual Corpus"

datasets:

- "projecte-aina/tecla"  

metrics:
- accuracy

model-index:
- name: roberta-base-ca-cased-tc
  results:
  - task:
      type: text-classification
    dataset:
      name: tecla
      type: projecte-aina/tecla
    metrics:
      - name: Accuracy
        type: accuracy
        value: 0.740388810634613

widget:

- text: "Els Pets presenten el seu nou treball al Palau Sant Jordi." 

- text: "Els barcelonins incrementen un 23% l’ús del cotxe des de l’inici de la pandèmia."

- text: "Retards a quatre línies de Rodalies per una avaria entre Sants i plaça de Catalunya."

- text: "Majors de 60 anys i sanitaris començaran a rebre la tercera dosi de la vacuna covid els propers dies."

- text: "Els cinemes Verdi estrenen Verdi Classics, un nou canal de televisió."

---

# Catalan BERTa (RoBERTa-base) finetuned for Text Classification.

The **roberta-base-ca-cased-tc** is a Text Classification (TC) model for the Catalan language fine-tuned from the [BERTa](https://huggingface.co/PlanTL-GOB-ES/roberta-base-ca) model, a [RoBERTa](https://arxiv.org/abs/1907.11692) base model pre-trained on a medium-size corpus collected from publicly available corpora and crawlers (check the BERTa model card for more details).

## Datasets
We used the TC dataset in Catalan called [TeCla](https://huggingface.co/datasets/projecte-aina/viquiquad) for training and evaluation.

## Evaluation and results
We evaluated the _roberta-base-ca-cased-tc_ on the TeCla test set against standard multilingual and monolingual baselines:

| Model        | TeCla (accuracy) | 
| ------------|:-------------|
| roberta-base-ca-cased-tc | **74.04** |
| mBERT       |  70.56 | 
| XLM-RoBERTa | 71.68 | 
| WikiBERT-ca |  73.22 | 

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