---
tags:
- Transformers
- token-classification
- sequence-tagger-model
language: fr
datasets:
- qanastek/ANTILLES
widget:
- text: "George Washington est allé à Washington"
---

# POET: A French Extended Part-of-Speech Tagger

- Corpora: [ANTILLES](https://github.com/qanastek/ANTILLES)
- Embeddings & Sequence Labelling: [CamemBERT](https://arxiv.org/abs/1911.03894)
- Number of Epochs: 115

**People Involved**

* [LABRAK Yanis](https://www.linkedin.com/in/yanis-labrak-8a7412145/) (1)
* [DUFOUR Richard](https://cv.archives-ouvertes.fr/richard-dufour) (2)

**Affiliations**

1. [LIA, NLP team](https://lia.univ-avignon.fr/), Avignon University, Avignon, France.
2. [LS2N, TALN team](https://www.ls2n.fr/equipe/taln/), Nantes University, Nantes, France.

## Demo: How to use in HuggingFace Transformers

Requires [transformers](https://pypi.org/project/transformers/): ```pip install transformers```

```python
from transformers import CamembertTokenizer, CamembertForTokenClassification, TokenClassificationPipeline

tokenizer = CamembertTokenizer.from_pretrained('qanastek/pos-french-camembert')
model = CamembertForTokenClassification.from_pretrained('qanastek/pos-french-camembert')
pos = TokenClassificationPipeline(model=model, tokenizer=tokenizer)

def make_prediction(sentence):
    labels = [l['entity'] for l in pos(sentence)]
    return list(zip(sentence.split(" "), labels))

res = make_prediction("George Washington est allé à Washington")
```

Output:

![Preview Output](preview.PNG)

## Training data

`ANTILLES` is a part-of-speech tagging corpora based on [UD_French-GSD](https://universaldependencies.org/treebanks/fr_gsd/index.html) which was originally created in 2015 and is based on the [universal dependency treebank v2.0](https://github.com/ryanmcd/uni-dep-tb).

Originally, the corpora consists of 400,399 words (16,341 sentences) and had 17 different classes. Now, after applying our tags augmentation we obtain 60 different classes which add linguistic and semantic information such as the gender, number, mood, person, tense or verb form given in the different CoNLL-03 fields from the original corpora.

We based our tags on the level of details given by the [LIA_TAGG](http://pageperso.lif.univ-mrs.fr/frederic.bechet/download.html) statistical POS tagger written by [Frédéric Béchet](http://pageperso.lif.univ-mrs.fr/frederic.bechet/index-english.html) in 2001.

The corpora used for this model is available on [Github](https://github.com/qanastek/ANTILLES) at the [CoNLL-U format](https://universaldependencies.org/format.html).

Training data are fed to the model as free language and doesn't pass a normalization phase. Thus, it's made the model case and punctuation sensitive.

## Original Tags

```plain
PRON VERB SCONJ ADP CCONJ DET NOUN ADJ AUX ADV PUNCT PROPN NUM SYM PART X INTJ
```

## New additional POS tags

| Abbreviation | Description | Examples |
|:--------:|:--------:|:--------:|
| PREP | Preposition | de |
| AUX | Auxiliary Verb | est |
| ADV | Adverb | toujours |
| COSUB | Subordinating conjunction | que |
| COCO | Coordinating Conjunction | et |
| PART | Demonstrative particle | -t |
| PRON | Pronoun | qui ce quoi |
| PDEMMS | Demonstrative Pronoun - Singular Masculine | ce |
| PDEMMP | Demonstrative Pronoun - Plural Masculine | ceux |
| PDEMFS | Demonstrative Pronoun - Singular Feminine | cette |
| PDEMFP | Demonstrative Pronoun - Plural Feminine | celles |
| PINDMS | Indefinite Pronoun - Singular Masculine | tout |
| PINDMP | Indefinite Pronoun - Plural Masculine | autres |
| PINDFS | Indefinite Pronoun - Singular Feminine | chacune |
| PINDFP | Indefinite Pronoun - Plural Feminine | certaines |
| PROPN | Proper noun | Houston |
| XFAMIL | Last name | Levy |
| NUM | Numerical Adjective | trentaine vingtaine |
| DINTMS | Masculine Numerical Adjective | un |
| DINTFS | Feminine Numerical Adjective | une |
| PPOBJMS | Pronoun complements of objects - Singular Masculine | le lui |
| PPOBJMP | Pronoun complements of objects - Plural Masculine | eux y |
| PPOBJFS | Pronoun complements of objects - Singular Feminine | moi la |
| PPOBJFP | Pronoun complements of objects - Plural Feminine | en y |
| PPER1S | Personal Pronoun First-Person - Singular | je |
| PPER2S | Personal Pronoun Second-Person - Singular | tu |
| PPER3MS | Personal Pronoun Third-Person - Singular Masculine | il |
| PPER3MP | Personal Pronoun Third-Person - Plural Masculine | ils |
| PPER3FS | Personal Pronoun Third-Person - Singular Feminine | elle |
| PPER3FP | Personal Pronoun Third-Person - Plural Feminine | elles |
| PREFS | Reflexive Pronoun First-Person - Singular | me m' |
| PREF | Reflexive Pronoun Third-Person - Singular | se s' |
| PREFP | Reflexive Pronoun First / Second-Person - Plural | nous vous |
| VERB | Verb | obtient |
| VPPMS | Past Participle - Singular Masculine | formulé |
| VPPMP | Past Participle - Plural Masculine | classés |
| VPPFS | Past Participle - Singular Feminine | appelée |
| VPPFP | Past Participle - Plural Feminine | sanctionnées |
| DET | Determinant | les l' |
| DETMS | Determinant - Singular Masculine | les |
| DETFS | Determinant - Singular Feminine | la |
| ADJ | Adjective | capable sérieux |
| ADJMS | Adjective - Singular Masculine | grand important |
| ADJMP | Adjective - Plural Masculine | grands petits |
| ADJFS | Adjective - Singular Feminine | française petite |
| ADJFP | Adjective - Plural Feminine | légères petites |
| NOUN | Noun | temps |
| NMS | Noun - Singular Masculine | drapeau |
| NMP | Noun - Plural Masculine | journalistes |
| NFS | Noun - Singular Feminine | tête |
| NFP | Noun - Plural Feminine | ondes |
| PREL | Relative Pronoun | qui dont |
| PRELMS | Relative Pronoun - Singular Masculine | lequel |
| PRELMP | Relative Pronoun - Plural Masculine | lesquels |
| PRELFS | Relative Pronoun - Singular Feminine | laquelle |
| PRELFP | Relative Pronoun - Plural Feminine | lesquelles |
| INTJ | Interjection | merci bref |
| CHIF | Numbers | 1979 10 |
| SYM | Symbol | € % |
| YPFOR | Endpoint | . |
| PUNCT | Ponctuation | : , |
| MOTINC | Unknown words | Technology Lady |
| X | Typos & others | sfeir 3D statu |

## Evaluation results

The test corpora used for this evaluation is available on [Github](https://github.com/qanastek/ANTILLES/blob/main/ANTILLES/test.conllu).

```plain
              precision    recall  f1-score   support

         ADJ     0.9040    0.8828    0.8933       128
       ADJFP     0.9811    0.9585    0.9697       434
       ADJFS     0.9606    0.9826    0.9715       918
       ADJMP     0.9613    0.9357    0.9483       451
       ADJMS     0.9561    0.9611    0.9586       952
         ADV     0.9870    0.9948    0.9908      1524
         AUX     0.9956    0.9964    0.9960      1124
        CHIF     0.9798    0.9774    0.9786      1239
        COCO     1.0000    0.9989    0.9994       884
       COSUB     0.9939    0.9939    0.9939       328
         DET     0.9972    0.9972    0.9972      2897
       DETFS     0.9990    1.0000    0.9995      1007
       DETMS     1.0000    0.9993    0.9996      1426
      DINTFS     0.9967    0.9902    0.9934       306
      DINTMS     0.9923    0.9948    0.9935       387
        INTJ     0.8000    0.8000    0.8000         5
      MOTINC     0.5049    0.5827    0.5410       266
         NFP     0.9807    0.9675    0.9740       892
         NFS     0.9778    0.9699    0.9738      2588
         NMP     0.9687    0.9495    0.9590      1367
         NMS     0.9759    0.9560    0.9659      3181
        NOUN     0.6164    0.8673    0.7206       113
         NUM     0.6250    0.8333    0.7143         6
        PART     1.0000    0.9375    0.9677        16
      PDEMFP     1.0000    1.0000    1.0000         3
      PDEMFS     1.0000    1.0000    1.0000        89
      PDEMMP     1.0000    1.0000    1.0000        20
      PDEMMS     1.0000    1.0000    1.0000       222
      PINDFP     1.0000    1.0000    1.0000         3
      PINDFS     0.8571    1.0000    0.9231        12
      PINDMP     0.9000    1.0000    0.9474         9
      PINDMS     0.9286    0.9701    0.9489        67
      PINTFS     0.0000    0.0000    0.0000         2
      PPER1S     1.0000    1.0000    1.0000        62
      PPER2S     0.7500    1.0000    0.8571         3
     PPER3FP     1.0000    1.0000    1.0000         9
     PPER3FS     1.0000    1.0000    1.0000        96
     PPER3MP     1.0000    1.0000    1.0000        31
     PPER3MS     1.0000    1.0000    1.0000       377
     PPOBJFP     1.0000    0.7500    0.8571         4
     PPOBJFS     0.9167    0.8919    0.9041        37
     PPOBJMP     0.7500    0.7500    0.7500        12
     PPOBJMS     0.9371    0.9640    0.9504       139
        PREF     1.0000    1.0000    1.0000       332
       PREFP     1.0000    1.0000    1.0000        64
       PREFS     1.0000    1.0000    1.0000        13
        PREL     0.9964    0.9964    0.9964       277
      PRELFP     1.0000    1.0000    1.0000         5
      PRELFS     0.8000    1.0000    0.8889         4
      PRELMP     1.0000    1.0000    1.0000         3
      PRELMS     1.0000    1.0000    1.0000        11
        PREP     0.9971    0.9977    0.9974      6161
        PRON     0.9836    0.9836    0.9836        61
       PROPN     0.9468    0.9503    0.9486      4310
       PUNCT     1.0000    1.0000    1.0000      4019
         SYM     0.9394    0.8158    0.8732        76
        VERB     0.9956    0.9921    0.9938      2273
       VPPFP     0.9145    0.9469    0.9304       113
       VPPFS     0.9562    0.9597    0.9580       273
       VPPMP     0.8827    0.9728    0.9256       147
       VPPMS     0.9778    0.9794    0.9786       630
       VPPRE     0.0000    0.0000    0.0000         1
           X     0.9604    0.9935    0.9766      1073
      XFAMIL     0.9386    0.9113    0.9248      1342
       YPFOR     1.0000    1.0000    1.0000      2750

    accuracy                         0.9778     47574
   macro avg     0.9151    0.9285    0.9202     47574
weighted avg     0.9785    0.9778    0.9780     47574
```

## BibTeX Citations

Please cite the following paper when using this model.

UD_French-GSD corpora:

```latex
@misc{
    universaldependencies,
    title={UniversalDependencies/UD_French-GSD},
    url={https://github.com/UniversalDependencies/UD_French-GSD}, journal={GitHub},
    author={UniversalDependencies}
}
```

LIA TAGG:

```latex
@techreport{LIA_TAGG,
  author = {Frédéric Béchet},
  title = {LIA_TAGG: a statistical POS tagger + syntactic bracketer},
  institution = {Aix-Marseille University & CNRS},
  year = {2001}
}
```

Flair Embeddings:

```latex
@inproceedings{akbik2018coling,
  title={Contextual String Embeddings for Sequence Labeling},
  author={Akbik, Alan and Blythe, Duncan and Vollgraf, Roland},
  booktitle = {{COLING} 2018, 27th International Conference on Computational Linguistics},
  pages     = {1638--1649},
  year      = {2018}
}
```

## Acknowledgment

This work was financially supported by [Zenidoc](https://zenidoc.fr/)
