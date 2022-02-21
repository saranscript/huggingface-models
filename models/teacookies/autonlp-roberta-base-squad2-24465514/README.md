---
tags:
- autonlp
- question-answering
language: unk
widget:
- text: "Who loves AutoNLP?"
  context: "Everyone loves AutoNLP"
datasets:
- teacookies/autonlp-data-roberta-base-squad2
co2_eq_emissions: 54.44076291568145
---

# Model Trained Using AutoNLP

- Problem type: Extractive Question Answering
- Model ID: 24465514
- CO2 Emissions (in grams): 54.44076291568145

## Validation Metrics

- Loss: 0.5786784887313843

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"question": "Who loves AutoNLP?", "context": "Everyone loves AutoNLP"}' https://api-inference.huggingface.co/models/teacookies/autonlp-roberta-base-squad2-24465514
```

Or Python API:

```
import torch

from transformers import AutoModelForQuestionAnswering, AutoTokenizer

model = AutoModelForQuestionAnswering.from_pretrained("teacookies/autonlp-roberta-base-squad2-24465514", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("teacookies/autonlp-roberta-base-squad2-24465514", use_auth_token=True)

from transformers import BertTokenizer, BertForQuestionAnswering

question, text = "Who loves AutoNLP?", "Everyone loves AutoNLP"

inputs = tokenizer(question, text, return_tensors='pt')

start_positions = torch.tensor([1])

end_positions = torch.tensor([3])

outputs = model(**inputs, start_positions=start_positions, end_positions=end_positions)

loss = outputs.loss

start_scores = outputs.start_logits

end_scores = outputs.end_logits
```