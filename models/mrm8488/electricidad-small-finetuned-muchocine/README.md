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
# Electricidad-small fine-tuned for (Spanish) Sentiment Anlalysis 🎞️👍👎


[Electricidad](https://huggingface.co/mrm8488/electricidad-small-discriminator) small fine-tuned on [muchocine](https://huggingface.co/datasets/muchocine) dataset for Spanish **Sentiment Analysis** downstream task.
## Fast usage with `pipelines`  🚀

```python
# pip install -q transformers

from transformers import AutoModelForSequenceClassification, AutoTokenizer

CHKPT = 'mrm8488/electricidad-small-finetuned-muchocine'
model = AutoModelForSequenceClassification.from_pretrained(CHKPT)
tokenizer = AutoTokenizer.from_pretrained(CHKPT)

from transformers import pipeline
classifier = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)

# It ranks your comments between 1 and 5 (stars)

classifier('Es una obra mestra. Brillante.')

classifier('Es una película muy buena.')

classifier('Una buena película, sin más.')

classifier('Esperaba mucho más.')

classifier('He tirado el dinero. Una basura. Vergonzoso.')
```