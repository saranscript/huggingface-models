# Classifying Text into NACE Codes

This model is [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) fine-tuned to classify descriptions of activities into [NACE Rev. 2](https://ec.europa.eu/eurostat/web/nace-rev2) codes.


## Data
The data used to fine-tune the model consist of 2.5 million descriptions of activities from Norwegian and Danish businesses. To improve the model's multilingual performance, random samples of the Norwegian and Danish descriptions were machine translated into the following languages:
- English
- German
- Spanish
- French
- Finnish
- Polish


## Quick Start

```python
from transformers import pipeline, AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("erst/xlm-roberta-base-finetuned-nace")
model = AutoModelForSequenceClassification.from_pretrained("erst/xlm-roberta-base-finetuned-nace")

pl = pipeline(
    "sentiment-analysis",
    model=model,
    tokenizer=tokenizer,
    return_all_scores=False,
)

pl("The purpose of our company is to build houses")
```
