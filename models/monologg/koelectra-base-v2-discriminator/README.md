---
language: ko
license: apache-2.0
tags:
  - korean
---

# KoELECTRA v2 (Base Discriminator)

Pretrained ELECTRA Language Model for Korean (`koelectra-base-v2-discriminator`)

For more detail, please see [original repository](https://github.com/monologg/KoELECTRA/blob/master/README_EN.md).

## Usage

### Load model and tokenizer

```python
>>> from transformers import ElectraModel, ElectraTokenizer

>>> model = ElectraModel.from_pretrained("monologg/koelectra-base-v2-discriminator")
>>> tokenizer = ElectraTokenizer.from_pretrained("monologg/koelectra-base-v2-discriminator")
```

### Tokenizer example

```python
>>> from transformers import ElectraTokenizer
>>> tokenizer = ElectraTokenizer.from_pretrained("monologg/koelectra-base-v2-discriminator")
>>> tokenizer.tokenize("[CLS] 한국어 ELECTRA를 공유합니다. [SEP]")
['[CLS]', '한국어', 'EL', '##EC', '##TRA', '##를', '공유', '##합니다', '.', '[SEP]']
>>> tokenizer.convert_tokens_to_ids(['[CLS]', '한국어', 'EL', '##EC', '##TRA', '##를', '공유', '##합니다', '.', '[SEP]'])
[2, 5084, 16248, 3770, 19059, 29965, 2259, 10431, 5, 3]
```

## Example using ElectraForPreTraining

```python
import torch
from transformers import ElectraForPreTraining, ElectraTokenizer

discriminator = ElectraForPreTraining.from_pretrained("monologg/koelectra-base-v2-discriminator")
tokenizer = ElectraTokenizer.from_pretrained("monologg/koelectra-base-v2-discriminator")

sentence = "나는 방금 밥을 먹었다."
fake_sentence = "나는 내일 밥을 먹었다."

fake_tokens = tokenizer.tokenize(fake_sentence)
fake_inputs = tokenizer.encode(fake_sentence, return_tensors="pt")

discriminator_outputs = discriminator(fake_inputs)
predictions = torch.round((torch.sign(discriminator_outputs[0]) + 1) / 2)

print(list(zip(fake_tokens, predictions.tolist()[1:-1])))
```
