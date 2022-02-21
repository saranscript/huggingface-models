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


# IcelandicNER DistilBERT

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
|      Date     |  0.969309 | 0.973042 | 0.971172 |  779.0  |
|    Location   |  0.941221 | 0.946929 | 0.944067 |  1319.0 |
| Miscellaneous |  0.848283 | 0.819251 | 0.833515 |  935.0  |
|     Money     |  0.928571 | 0.934641 | 0.931596 |  153.0  |
|  Organization |  0.874147 | 0.876806 | 0.875475 |  1315.0 |
|    Percent    |  1.000000 | 1.000000 | 1.000000 |  108.0  |
|     Person    |  0.956674 | 0.972853 | 0.964695 |  2247.0 |
|      Time     |  0.965318 | 0.970930 | 0.968116 |  172.0  |
|   micro avg   |  0.926110 | 0.929141 | 0.927623 |  7028.0 |
|   macro avg   |  0.935441 | 0.936807 | 0.936079 |  7028.0 |
|  weighted avg |  0.925578 | 0.929141 | 0.927301 |  7028.0 |


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


model_name_or_path = "m3hrdadfi/icelandic-ner-distilbert" 
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
