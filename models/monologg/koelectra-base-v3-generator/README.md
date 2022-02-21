---
language: ko
license: apache-2.0
tags:
  - korean
---

# KoELECTRA v3 (Base Generator)

Pretrained ELECTRA Language Model for Korean (`koelectra-base-v3-generator`)

For more detail, please see [original repository](https://github.com/monologg/KoELECTRA/blob/master/README_EN.md).

## Usage

### Load model and tokenizer

```python
>>> from transformers import ElectraModel, ElectraTokenizer

>>> model = ElectraModel.from_pretrained("monologg/koelectra-base-v3-generator")
>>> tokenizer = ElectraTokenizer.from_pretrained("monologg/koelectra-base-v3-generator")
```

### Tokenizer example

```python
>>> from transformers import ElectraTokenizer
>>> tokenizer = ElectraTokenizer.from_pretrained("monologg/koelectra-base-v3-generator")
>>> tokenizer.tokenize("[CLS] 한국어 ELECTRA를 공유합니다. [SEP]")
['[CLS]', '한국어', 'EL', '##EC', '##TRA', '##를', '공유', '##합니다', '.', '[SEP]']
>>> tokenizer.convert_tokens_to_ids(['[CLS]', '한국어', 'EL', '##EC', '##TRA', '##를', '공유', '##합니다', '.', '[SEP]'])
[2, 11229, 29173, 13352, 25541, 4110, 7824, 17788, 18, 3]
```

## Example using ElectraForMaskedLM

```python
from transformers import pipeline

fill_mask = pipeline(
    "fill-mask",
    model="monologg/koelectra-base-v3-generator",
    tokenizer="monologg/koelectra-base-v3-generator"
)

print(fill_mask("나는 {} 밥을 먹었다.".format(fill_mask.tokenizer.mask_token)))
```
