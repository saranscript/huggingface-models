# Classifying Text into DB07 Codes

This model is [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) fine-tuned to classify Danish descriptions of activities into [Dansk Branchekode DB07](https://www.dst.dk/en/Statistik/dokumentation/nomenklaturer/dansk-branchekode-db07) codes.


## Data
Approximately 2.5 million business names and descriptions of activities from Norwegian and Danish businesses were used to fine-tune the model. The Norwegian descriptions were translated into Danish and the Norwegian SN 2007 codes were translated into Danish DB07 codes.

Activity descriptions and business names were concatenated but separated by the separator token `</s>`. Thus, the model was trained on input texts in the format `f"{description_of_activity}</s>{business_name}"`.

## Quick Start

```python
from transformers import pipeline, AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("erst/xlm-roberta-base-finetuned-db07")
model = AutoModelForSequenceClassification.from_pretrained("erst/xlm-roberta-base-finetuned-db07")

pl = pipeline(
    "sentiment-analysis",
    model=model,
    tokenizer=tokenizer,
    return_all_scores=False,
)

pl("Vi sælger sko")

pl("We sell clothes</s>Clothing ApS")
```
