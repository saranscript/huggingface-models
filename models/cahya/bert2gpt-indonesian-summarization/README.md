---
language: id
tags:
- pipeline:summarization
- summarization
- bert2gpt
datasets:
- id_liputan6
license: apache-2.0
---

# Indonesian BERT2BERT Summarization Model

Finetuned EncoderDecoder model using BERT-base and GPT2-small for Indonesian text summarization.

## Finetuning Corpus

`bert2gpt-indonesian-summarization` model is based on `cahya/bert-base-indonesian-1.5G` and `cahya/gpt2-small-indonesian-522M`by [cahya](https://huggingface.co/cahya), finetuned using [id_liputan6](https://huggingface.co/datasets/id_liputan6) dataset.

## Load Finetuned Model

```python
from transformers import BertTokenizer, EncoderDecoderModel

tokenizer = BertTokenizer.from_pretrained("cahya/bert2gpt-indonesian-summarization")
tokenizer.bos_token = tokenizer.cls_token
tokenizer.eos_token = tokenizer.sep_token
model = EncoderDecoderModel.from_pretrained("cahya/bert2gpt-indonesian-summarization")
```

## Code Sample

```python
from transformers import BertTokenizer, EncoderDecoderModel

tokenizer = BertTokenizer.from_pretrained("cahya/bert2gpt-indonesian-summarization")
tokenizer.bos_token = tokenizer.cls_token
tokenizer.eos_token = tokenizer.sep_token
model = EncoderDecoderModel.from_pretrained("cahya/bert2gpt-indonesian-summarization")

# 
ARTICLE_TO_SUMMARIZE = ""

# generate summary
input_ids = tokenizer.encode(ARTICLE_TO_SUMMARIZE, return_tensors='pt')
summary_ids = model.generate(input_ids,
            min_length=20,
            max_length=80, 
            num_beams=10,
            repetition_penalty=2.5, 
            length_penalty=1.0, 
            early_stopping=True,
            no_repeat_ngram_size=2,
            use_cache=True,
            do_sample = True,
            temperature = 0.8,
            top_k = 50,
            top_p = 0.95)

summary_text = tokenizer.decode(summary_ids[0], skip_special_tokens=True)
print(summary_text)
```

Output:

```

```

