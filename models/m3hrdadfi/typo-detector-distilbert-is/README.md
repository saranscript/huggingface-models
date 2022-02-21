---
language: is
widget:
- text: Páli, vini mínum, langaði að horfa á sjónnvarpið.
- text: "Leggir þciðursins eru þaktir fjöðrum til bað edravn fuglnn gekgn kuldanué ."
- text: "Þar hitta þeir konu Björns og segir ovs :"
- text: "Ingvar Sæmundsson ekgk rú sveitinni árið 2015 og etnbeitii sér að hinni þungarokkssvedt svnni Momentum ."
- text: "Þar hitta þeir konu Björns og segir ovs :"
- text: "Var hann síðaún hkluti af leikhópnum sem ferðaðist um Bandaríkin til að sýan söngleikinn ."
 
---

# Typo Detector For Icelandic 🇮🇸


## Dataset Information

Synthetic data for this specific task.

## Evaluation

The following tables summarize the scores obtained by model overall and per each class.

|       #      | precision |  recall  | f1-score | support |
|:------------:|:---------:|:--------:|:--------:|:-------:|
|     TYPO     |  0.98954  | 0.967603 | 0.978448 | 43800.0 |
|   micro avg  |  0.98954  | 0.967603 | 0.978448 | 43800.0 |
|   macro avg  |  0.98954  | 0.967603 | 0.978448 | 43800.0 |
| weighted avg |  0.98954  | 0.967603 | 0.978448 | 43800.0 |


## How to use

You use this model with Transformers pipeline for NER (token-classification).

### Installing requirements

```bash
pip install transformers
```

### Prediction using pipeline

```python
import torch
from transformers import AutoConfig, AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline


model_name_or_path = "m3hrdadfi/typo-detector-distilbert-is"
config = AutoConfig.from_pretrained(model_name_or_path)
tokenizer = AutoTokenizer.from_pretrained(model_name_or_path)
model = AutoModelForTokenClassification.from_pretrained(model_name_or_path, config=config)
nlp = pipeline('token-classification', model=model, tokenizer=tokenizer, aggregation_strategy="average")
```

```python
sentences = [
"Páli, vini mínum, langaði að horfa á sjónnvarpið.",
"Leggir þciðursins eru þaktir fjöðrum til bað edravn fuglnn gekgn kuldanué .",
"Þar hitta þeir konu Björns og segir ovs :",
"Ingvar Sæmundsson ekgk rú sveitinni árið 2015 og etnbeitii sér að hinni þungarokkssvedt svnni Momentum .",
"Þar hitta þeir konu Björns og segir ovs :",
"Var hann síðaún hkluti af leikhópnum sem ferðaðist um Bandaríkin til að sýan söngleikinn ."
]

for sentence in sentences:
    typos = [sentence[r["start"]: r["end"]] for r in nlp(sentence)]

    detected = sentence
    for typo in typos:
        detected = detected.replace(typo, f'<i>{typo}</i>')

    print("   [Input]: ", sentence)
    print("[Detected]: ", detected)
    print("-" * 130)
```

Output:
```text
   [Input]:  Páli, vini mínum, langaði að horfa á sjónnvarpið.
[Detected]:  Páli, vini mínum, langaði að horfa á <i>sjónnvarpið</i>.
----------------------------------------------------------------------------------------------------------------------------------
   [Input]:  Leggir þciðursins eru þaktir fjöðrum til bað edravn fuglnn gekgn kuldanué .
[Detected]:  Leggir <i>þciðursins</i> eru þaktir fjöðrum til <i>bað</i> <i>edravn</i> <i>fuglnn</i> <i>gekgn</i> <i>kuldanué</i> .
----------------------------------------------------------------------------------------------------------------------------------
   [Input]:  Þar hitta þeir konu Björns og segir ovs :
[Detected]:  Þar hitta þeir konu Björns og segir <i>ovs</i> :
----------------------------------------------------------------------------------------------------------------------------------
   [Input]:  Ingvar Sæmundsson ekgk rú sveitinni árið 2015 og etnbeitii sér að hinni þungarokkssvedt svnni Momentum .
[Detected]:  Ingvar Sæmundsson <i>ekgk</i> <i>rú</i> sveitinni árið 2015 og <i>etnbeitii</i> sér að hinni <i>þungarokkssvedt</i> <i>svnni</i> Momentum .
----------------------------------------------------------------------------------------------------------------------------------
   [Input]:  Þar hitta þeir konu Björns og segir ovs :
[Detected]:  Þar hitta þeir konu Björns og segir <i>ovs</i> :
----------------------------------------------------------------------------------------------------------------------------------
   [Input]:  Var hann síðaún hkluti af leikhópnum sem ferðaðist um Bandaríkin til að sýan söngleikinn .
[Detected]:  Var hann <i>síðaún</i> <i>hkluti</i> af leikhópnum sem ferðaðist um Bandaríkin til að <i>sýan</i> söngleikinn .
----------------------------------------------------------------------------------------------------------------------------------
```

## Questions?
Post a Github issue on the [TypoDetector Issues](https://github.com/m3hrdadfi/typo-detector/issues) repo.