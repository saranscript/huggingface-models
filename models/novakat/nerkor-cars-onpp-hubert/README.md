---

language: 
  - hu
tags:
- token-classification
license: gpl
metrics:
- F1
widget:
- text: "A jótékonysági szervezet által idézett Forbes-adatok szerint a világ tíz leggazdagabb embere: Elon Musk (Tesla, SpaceX), Jeff Bezos (Amazon, Blue Origin), Bernard Arnault és családja (LVMH, azaz Louis Vuitton és Moët Hennessy), Bill Gates (Microsoft), Larry Ellison (Oracle), Larry Page (Google), Sergey Brin (Google), Mark Zuckerberg (Facebook), Steve Ballmer (Microsoft) és Warren Buffett (befektető).
Miközben vagyonuk együttesen 700 milliárdról másfél ezer milliárd dollárra nőtt 2020 márciusa és 2021 novembere között, jelentős eltérések vannak közöttük: Musk vagyona több mint 1000 százalékos, míg Gatesé szerényebb, 30 százalékos növekedést mutatott."
inference:
  parameters:
    aggregation_strategy: "first"

---

# Hungarian named entity recognition model with OntoNotes5 + more entity types

  - Pretrained model used: SZTAKI-HLT/hubert-base-cc 
  - Finetuned on NerKor+CARS-ONPP Corpus
  	
## Limitations

- max_seq_length = 448

## Training data

The underlying corpus, [NerKor+CARS-ONPP](https://github.com/novakat/NYTK-NerKor-Cars-OntoNotesPP), was derived from [NYTK-NerKor](https://github.com/nytud/NYTK-NerKor), a Hungarian gold standard named entity annotated corpus containing about 1 million tokens. 
It includes a small addition of 12k tokens of text (individual sentences) concerning motor vehicles (cars, buses, motorcycles) from the news archive of [hvg.hu](hvg.hu).
While the annotation in NYTK-NerKor followed the CoNLL2002 labelling standard with just four NE categories (`PER`, `LOC`, `MISC`, `ORG`), this version of the corpus features over 30 entity types, including all entity types used in the [OntoNotes 5.0] English NER annotation.
The new annotation elaborates on subtypes of the `LOC` and `MISC` entity types, and includes annotation for non-names like times and dates, quantities, languages and nationalities or religious or political groups. The annotation was elaborated with further entity subtypes not present in the Ontonotes 5 annotation (see below).

## Tags derived from the OntoNotes 5.0 annotation

Names are annotated according to the following set of types:

| | | 
|---|---------|
|`PER` | = PERSON People, including fictional |
|`FAC` | = FACILITY Buildings, airports, highways, bridges, etc. |
|`ORG` | = ORGANIZATION Companies, agencies, institutions, etc. |
|`GPE` | Geopolitical entites: countries, cities, states |
|`LOC` | = LOCATION Non-GPE locations, mountain ranges, bodies of water |
|`PROD` | = PRODUCT Vehicles, weapons, foods, etc. (Not services) |
|`EVENT` | Named hurricanes, battles, wars, sports events, etc. |
|`WORK_OF_ART` | Titles of books, songs, etc. |
|`LAW` | Named documents made into laws  |

The following are also annotated in a style similar to names:

| | | 
|---|---------|
| `NORP` | Nationalities or religious or political groups |
| `LANGUAGE` | Any named language |
| `DATE` | Absolute or relative dates or periods |
| `TIME` | Times smaller than a day |
| `PERCENT` | Percentage (including "%") |
| `MONEY` | Monetary values, including unit |
| `QUANTITY` | Measurements, as of weight or distance |
| `ORDINAL` | "first", "second" |
| `CARDINAL` | Numerals that do not fall under another type |

## Additional tags (not in OntoNotes 5)
Further subtypes of names of type `MISC`:

| | |
|-|-|
|`AWARD`| Awards and prizes |
| `CAR` | Cars and trucks |
|`MEDIA`| Media outlets, TV channels, news portals|
|`SMEDIA`| Social media platforms|
|`PROJ`| Projects and initiatives |
|`MISC`| Unresolved subtypes of MISC entities |
|`MISC-ORG`| Organization-like unresolved subtypes of MISC entities |

Further non-name entities:

| | |
|-|-|
|`DUR` |Time duration
|`ID`| identifier