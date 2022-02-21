---
language: da
tags:
- danish
- bert
- question answering
- squad
- machine translation
- botxo
license: cc-by-4.0
datasets:
- common_crawl
- wikipedia
- dindebat.dk
- hestenettet.dk
- danish OpenSubtitles
widget:
- context: Stine sagde hej, men Jacob sagde halløj.
---

# Danish BERT (version 2, uncased) by [BotXO](https://github.com/botxo/nordic_bert) fine-tuned for Question Answering (QA) on the [machine-translated SQuAD-da dataset](https://github.com/ccasimiro88/TranslateAlignRetrieve/tree/multilingual/squads-tar/da) 



```python
from transformers import AutoTokenizer, AutoModelForQuestionAnswering

tokenizer = AutoTokenizer.from_pretrained("jacobshein/danish-bert-botxo-qa-squad")
model = AutoModelForQuestionAnswering.from_pretrained("jacobshein/danish-bert-botxo-qa-squad")

```

#### Contact

For further information on usage or fine-tuning procedure, please reach out by email through [jacobhein.com](https://jacobhein.com/#contact).
