---
tags:
- autonlp
- question-answering
language: unk
widget:
- text: "Who loves AutoNLP?"
  context: "Everyone loves AutoNLP"
datasets:
- teacookies/autonlp-data-more_fine_tune_24465520
co2_eq_emissions: 80.25874179679201
---

# Model Trained Using AutoNLP

- Problem type: Extractive Question Answering
- Model ID: 26265909
- CO2 Emissions (in grams): 80.25874179679201

## Validation Metrics

- Loss: 5.950643062591553

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"question": "Who loves AutoNLP?", "context": "Everyone loves AutoNLP"}' https://api-inference.huggingface.co/models/teacookies/autonlp-more_fine_tune_24465520-26265909
```

Or Python API:

```
import torch

from transformers import AutoModelForQuestionAnswering, AutoTokenizer

model = AutoModelForQuestionAnswering.from_pretrained("teacookies/autonlp-more_fine_tune_24465520-26265909", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("teacookies/autonlp-more_fine_tune_24465520-26265909", use_auth_token=True)

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