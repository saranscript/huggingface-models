---
language: ko
license: apache-2.0
tags:
  - korean
---

# KrELECTRA-base-mecab
Korean-based Pre-trained ELECTRA Language Model using Mecab (Morphological Analyzer)

## Usage

### Load model and tokenizer

```python
>>> from transformers import AutoTokenizer, AutoModelForPreTraining
>>> model = AutoModelForPreTraining.from_pretrained("Jinhwan/krelectra-base-mecab")
>>> tokenizer = AutoTokenizer.from_pretrained("Jinhwan/krelectra-base-mecab")
```

### Tokenizer example

```python
>>> from transformers import AutoTokenizer
>>> tokenizer = AutoTokenizer.from_pretrained("Jinhwan/krelectra-base-mecab")
>>> tokenizer.tokenize("[CLS] 한국어 ELECTRA를 공유합니다. [SEP]")
['[CLS]', '한국어', 'EL', '##ECT', '##RA', '##를', '공유', '##합', '##니다', '.', '[SEP]']
>>> tokenizer.convert_tokens_to_ids(['[CLS]', '한국어', 'EL', '##ECT', '##RA', '##를', '공유', '##합', '##니다', '.', '[SEP]'])
[2, 7214, 24023, 24663, 26580, 3195, 7086, 3746, 5500, 17, 3]
