---
language: ko
tags:
  - korean
mask_token: "[MASK]"
widget:
  - text: 대한민국의 수도는 [MASK] 입니다.
---

# KoBigBird

<img src="https://user-images.githubusercontent.com/28896432/140442206-e34b02d5-e279-47e5-9c2a-db1278b1c14d.png" width="200"/>

Pretrained BigBird Model for Korean (**kobigbird-bert-base**)

## About

BigBird, is a sparse-attention based transformer which extends Transformer based models, such as BERT to much longer sequences.

BigBird relies on **block sparse attention** instead of normal attention (i.e. BERT's attention) and can handle sequences up to a length of 4096 at a much lower compute cost compared to BERT.

Model is warm started from Korean BERT’s checkpoint.

## How to use

*NOTE:* Use `BertTokenizer` instead of BigBirdTokenizer. (`AutoTokenizer` will load `BertTokenizer`)

```python
from transformers import AutoModel, AutoTokenizer

# by default its in `block_sparse` mode with num_random_blocks=3, block_size=64
model = AutoModel.from_pretrained("monologg/kobigbird-bert-base")

# you can change `attention_type` to full attention like this:
model = AutoModel.from_pretrained("monologg/kobigbird-bert-base", attention_type="original_full")

# you can change `block_size` & `num_random_blocks` like this:
model = AutoModel.from_pretrained("monologg/kobigbird-bert-base", block_size=16, num_random_blocks=2)

tokenizer = AutoTokenizer.from_pretrained("monologg/kobigbird-bert-base")
text = "한국어 BigBird 모델을 공개합니다!"
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```
