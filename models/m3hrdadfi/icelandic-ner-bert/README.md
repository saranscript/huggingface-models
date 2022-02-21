---
language: is
license: apache-2.0
widget:
 - text: "Kristin manneskja getur ekki lagt frásagnir af Jesú Kristi á hilluna vegna þess að hún sé búin að lesa þær ."
 - text: "Til hvers að kjósa flokk , sem þykist vera Jafnaðarmannaflokkur rétt fyrir kosningar , þegar að það er hægt að kjósa sannnan jafnaðarmannaflokk , sjálfan Jafnaðarmannaflokk Íslands - Samfylkinguna ."
 - text: "Það sannaðist svo eftirminnilega á plötunni Það þarf fólk eins og þig sem kom út fyrir þremur árum , en á henni hann Fálka úr Keflavík og Gáluna , son sinn , til að útsetja lög hans og spila inn ."
 - text: "Lögin hafa áður komið út sem aukalög á smáskífum af Hail to the Thief , en á disknum er líka myndband og fleira efni fyrir tölvur ."
 - text: "Britney gerði honum viðvart og hann ók henni á UCLA-sjúkrahúsið í Santa Monica en það er í nágrenni hljóðversins ."
---


# IcelandicNER BERT

This model was fine-tuned on the MIM-GOLD-NER dataset for the Icelandic language. 
The [MIM-GOLD-NER](http://hdl.handle.net/20.500.12537/42) corpus was developed at [Reykjavik University](https://en.ru.is/) in 2018–2020 that covered eight types of entities:

- Date
- Location
- Miscellaneous 
- Money
- Organization
- Percent
- Person
- Time 

## Dataset Information

|       |   Records |   B-Date |   B-Location |   B-Miscellaneous |   B-Money |   B-Organization |   B-Percent |   B-Person |   B-Time |   I-Date |   I-Location |   I-Miscellaneous |   I-Money |   I-Organization |   I-Percent |   I-Person |   I-Time |
|:------|----------:|---------:|-------------:|------------------:|----------:|-----------------:|------------:|-----------:|---------:|---------:|-------------:|------------------:|----------:|-----------------:|------------:|-----------:|---------:|
| Train |     39988 |     3409 |         5980 |              4351 |       729 |             5754 |         502 |      11719 |      868 |     2112 |          516 |              3036 |       770 |             2382 |          50 |       5478 |      790 |
| Valid |      7063 |      570 |         1034 |               787 |       100 |             1078 |         103 |       2106 |      147 |      409 |           76 |               560 |       104 |              458 |           7 |        998 |      136 |
| Test  |      8299 |      779 |         1319 |               935 |       153 |             1315 |         108 |       2247 |      172 |      483 |          104 |               660 |       167 |              617 |          10 |       1089 |      158 |


## Evaluation

The following tables summarize the scores obtained by model overall and per each class.

|     entity    | precision |  recall  | f1-score | support |
|:-------------:|:---------:|:--------:|:--------:|:-------:|
|      Date     |  0.969466 | 0.978177 | 0.973802 |  779.0  |
|    Location   |  0.955201 | 0.953753 | 0.954476 |  1319.0 |
| Miscellaneous |  0.867033 | 0.843850 | 0.855285 |  935.0  |
|     Money     |  0.979730 | 0.947712 | 0.963455 |  153.0  |
|  Organization |  0.893939 | 0.897338 | 0.895636 |  1315.0 |
|    Percent    |  1.000000 | 1.000000 | 1.000000 |  108.0  |
|     Person    |  0.963028 | 0.973743 | 0.968356 |  2247.0 |
|      Time     |  0.976879 | 0.982558 | 0.979710 |  172.0  |
|   micro avg   |  0.938158 | 0.938958 | 0.938558 |  7028.0 |
|   macro avg   |  0.950659 | 0.947141 | 0.948840 |  7028.0 |
|  weighted avg |  0.937845 | 0.938958 | 0.938363 |  7028.0 |


## How To Use
You use this model with Transformers pipeline for NER.

### Installing requirements

```bash
pip install transformers
```

### How to predict using pipeline

```python
from transformers import AutoTokenizer
from transformers import AutoModelForTokenClassification  # for pytorch
from transformers import TFAutoModelForTokenClassification  # for tensorflow
from transformers import pipeline


model_name_or_path = "m3hrdadfi/icelandic-ner-bert" 
tokenizer = AutoTokenizer.from_pretrained(model_name_or_path)
model = AutoModelForTokenClassification.from_pretrained(model_name_or_path)  # Pytorch
# model = TFAutoModelForTokenClassification.from_pretrained(model_name_or_path)  # Tensorflow

nlp = pipeline("ner", model=model, tokenizer=tokenizer)
example = "Kristin manneskja getur ekki lagt frásagnir af Jesú Kristi á hilluna vegna þess að hún sé búin að lesa þær ."

ner_results = nlp(example)
print(ner_results)
```


## Questions?
Post a Github issue on the [IcelandicNER Issues](https://github.com/m3hrdadfi/icelandic-ner/issues) repo.
