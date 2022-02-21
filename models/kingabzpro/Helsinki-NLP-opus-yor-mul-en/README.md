---
language: Yorùbá
datasets:
- AI4D-Africa - Yorùbá Machine Translation Challenge
tags:
- text
- machine-translation
- language-translation
- seq2seq
- helsinki-nlp
license: apache-2.0
metrics:
- ROUGE
---
## Predicting English Translation
```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

# Loading tokenizer and model
tokenizer = AutoTokenizer.from_pretrained("kingabzpro/Helsinki-NLP-opus-yor-mul-en")
model = AutoModelForSeq2SeqLM.from_pretrained("kingabzpro/Helsinki-NLP-opus-yor-mul-en").to('cuda')

# Prediction
a = model.generate(**tokenizer.prepare_seq2seq_batch('Nínú ìpè kan lẹ́yìn ìgbà náà, wọ́n sọ fún aṣojú iléeṣẹ́ BlaBlaCar pé ètò náà ti yí padà, pé',return_tensors='pt').to('cuda'))
text = tokenizer.batch_decode(a)

# Cleaning text
text = str(text)
text = re.sub("<pad> ","",text)
text = re.sub("'","",text)
text = text.replace("[", "")
text = text.replace("]", "")
text
```
## Result
```
'In a statement after that hearing, the BualaCard’s representative was told that the event had changed, that he had turned up.'
```
## ROGUE Score
**0.3025**
