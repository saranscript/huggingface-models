---
language: is
widget:
- text: Má bjóða þér <mask> í kvöld?
- text: Forseti <mask> er ágæt.
- text: Súpan var <mask> á bragðið.
tags:
- roberta
- icelandic
- masked-lm
- pytorch
license: agpl-3.0
---

# IceBERT

IceBERT was trained with fairseq using the RoBERTa-base architecture. The training data used is shown in the table below.

| Dataset                                              | Size    | Tokens |
|------------------------------------------------------|---------|--------|
| Icelandic Gigaword Corpus v20.05 (IGC)               | 8.2 GB  | 1,388M |
| Icelandic Common Crawl Corpus (IC3)                  | 4.9 GB  | 824M   |
| Greynir News articles                                | 456 MB  | 76M    |
| Icelandic Sagas                                      | 9 MB    | 1.7M   |
| Open Icelandic e-books (Rafbókavefurinn)             | 14 MB   | 2.6M   |
| Data from the medical library of Landspitali         | 33 MB   | 5.2M   |
| Student theses from Icelandic universities (Skemman) | 2.2 GB  | 367M   |
| Total                                                | 15.8 GB | 2,664M |
