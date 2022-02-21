---
language: es
datasets:
- muchocine
widget:
- text: "Una buena película, sin más."
tags:
- sentiment
- analysis
- spanish

---
# Electricidad-base fine-tuned for (Spanish) Sentiment Anlalysis 🎞️👍👎


[Electricidad](https://huggingface.co/mrm8488/electricidad-base-discriminator) base fine-tuned on [muchocine](https://huggingface.co/datasets/muchocine) dataset for Spanish **Sentiment Analysis** downstream task.
## Fast usage with `pipelines`  🚀

```python
# pip install -q transformers

from transformers import AutoModelForSequenceClassification, AutoTokenizer

CHKPT = 'mrm8488/electricidad-base-finetuned-muchocine'
model = AutoModelForSequenceClassification.from_pretrained(CHKPT)
tokenizer = AutoTokenizer.from_pretrained(CHKPT)

from transformers import pipeline
classifier = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)

# It ranks your comments between 1 and 5 (stars)

classifier('Es una obra mestra. Brillante.')
# [{'label': '5', 'score': 0.9498381614685059}]

classifier('Es una película muy buena.')
# {'label': '4', 'score': 0.9277070760726929}]

classifier('Una buena película, sin más.')
# [{'label': '3', 'score': 0.9768431782722473}]

classifier('Esperaba mucho más.')
# [{'label': '2', 'score': 0.7063605189323425}]

classifier('He tirado el dinero. Una basura. Vergonzoso.')
# [{'label': '1', 'score': 0.8494752049446106}]
```