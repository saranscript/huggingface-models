---
language:
- ca
license: apache-2.0
tags:
- "catalan"
- "qa"
datasets:
- "xquad-ca"
- "viquiquad"  
metrics:
- "f1"
- "exact match"
widget:
- text: "Quan va començar el Super3?"
  context: "El Super3 o Club Super3 és un univers infantil català creat a partir d'un programa emès per Televisió de Catalunya des del 1991. Està format per un canal de televisió, la revista Súpers!, la Festa dels Súpers i un club que té un milió i mig de socis."
  
- text: "Quants eren els germans Marx?"
  context: "Els germans Marx van ser un grup de còmics dels Estats Units que originàriament estava compost per cinc germans (entre parèntesis els noms artístics): Leonard (Chico), Adolph (Harpo), Julius (Groucho), Milton (Gummo) i Herbert (Zeppo)."
  
- text: "On van ser els Jocs Olímpics de 1992?"
  context: "Els Jocs Olímpics d'estiu de 1992, oficialment Jocs Olímpics de la XXV Olimpíada, es van celebrar a la ciutat de Barcelona entre els dies 25 de juliol i 9 d'agost de 1992. Hi participaren 9.356 atletes (6.652 homes i 2.704 dones) de 169 comitès nacionals, que competiren en 32 esports i 286 especialitats."
  
- text: "Qui va dissenyar la Sagrada Família?"
  context: "El Temple Expiatori de la Sagrada Família, conegut habitualment com la Sagrada Família, és una basílica catòlica situada a la ciutat de Barcelona. És un dels exemples més coneguts del modernisme català i un edifici únic al món, que ha esdevingut tot un símbol de la ciutat. Obra inacabada de l'arquitecte català Antoni Gaudí, és al barri de la Sagrada Família, al districte de l'Eixample de la ciutat."
  
- text: "Quin és el tercer volcà més gran de la Terra?"
  context: "El Teide (o Pic del Teide) és un estratovolcà i muntanya de Tenerife, Illes Canàries (28.27 N, 16.6 O). Amb una altitud de 3718 m sobre el nivell del mar i amb aproximadament uns 7000 m sobre el llit marí adjacent, és la muntanya més alta d'Espanya, la muntanya més alta de totes les illes atlàntiques i el tercer volcà més gran de la Terra."


---

# Catalan BERTa (RoBERTa-base) finetuned for Question Answering.

The **roberta-base-ca-cased-qa** is a Question Answering (QA) model for the Catalan language fine-tuned from the [BERTa](https://huggingface.co/PlanTL-GOB-ES/roberta-base-ca) model, a [RoBERTa](https://arxiv.org/abs/1907.11692) base model pre-trained on a medium-size corpus collected from publicly available corpora and crawlers (check the BERTa model card for more details).

## Datasets
We used the QA dataset in Catalan called [ViquiQuAD](https://huggingface.co/datasets/projecte-aina/viquiquad) for training and evaluation, and the [XQuAD-ca](https://huggingface.co/datasets/projecte-aina/xquad-ca) test set for evaluation.

## Evaluation and results
We evaluated the _roberta-base-ca-cased-qa_ on the ViquiQuAD and XQuAD-ca test sets against standard multilingual and monolingual baselines:


| Model        | ViquiQuAD (F1/EM)  | XQuAD-ca (F1/EM) | 
| ------------|:-------------:| -----:|
| roberta-base-ca-cased-qa | **86.99/73.25** | **67.81/49.43**  |
| mBERT       | 86.97/72.22 | 67.15/46.51 |
| XLM-RoBERTa | 85.50/70.47 | 67.10/46.42 |
| WikiBERT-ca | 85.45/70.75 | 65.21/36.60  |

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