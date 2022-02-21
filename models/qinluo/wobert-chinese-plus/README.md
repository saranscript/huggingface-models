---
language: zh
tags:
- wobert
inference: True
---

## Word based BERT model

原模型及说明见：https://github.com/ZhuiyiTechnology/WoBERT

pytorch 模型见: https://github.com/JunnYu/WoBERT_pytorch

## 安装 WoBertTokenizer

```bash
pip install git+https://github.com/JunnYu/WoBERT_pytorch.git
```

## TF Example
```python
from transformers import TFBertForMaskedLM as WoBertForMaskedLM
from wobert import WoBertTokenizer

import tensorflow as tf

pretrained_model_or_path = 'qinluo/wobert-chinese-plus'

tokenizer = WoBertTokenizer.from_pretrained(pretrained_model_or_path)
model = WoBertForMaskedLM.from_pretrained(pretrained_model_or_path)

text = '今天[MASK]很好，我[MASK]去公园玩。'
inputs = tokenizer(text, return_tensors='tf')
outputs = model(**inputs).logits[0]

outputs_sentence = ''
for i, id in enumerate(tokenizer.encode(text)):
    if id == tokenizer.mask_token_id:
        tokens = tokenizer.convert_ids_to_tokens(tf.math.top_k(outputs[i], k=5)[1])
        outputs_sentence += '[' + '|'.join(tokens) + ']'
    else:
        outputs_sentence += ''.join(tokenizer.convert_ids_to_tokens([id], skip_special_tokens=True))

print(outputs_sentence)

# 今天[天气|阳光|天|心情|空气]很好，我[想|要|打算|准备|就]去公园玩。

```

## Pytorch Example
```python
from transformers import BertForMaskedLM as WoBertForMaskedLM
from wobert import WoBertTokenizer


pretrained_model_or_path = 'qinluo/wobert-chinese-plus'

tokenizer = WoBertTokenizer.from_pretrained(pretrained_model_or_path)
model = WoBertForMaskedLM.from_pretrained(pretrained_model_or_path)

text = '今天[MASK]很好，我[MASK]去公园玩。'
inputs = tokenizer(text, return_tensors='pt')
outputs = model(**inputs).logits[0]

outputs_sentence = ''
for i, id in enumerate(tokenizer.encode(text)):
    if id == tokenizer.mask_token_id:
        tokens = tokenizer.convert_ids_to_tokens(outputs[i].topk(k=5)[1])
        outputs_sentence += '[' + '|'.join(tokens) + ']'
    else:
        outputs_sentence += ''.join(tokenizer.convert_ids_to_tokens([id], skip_special_tokens=True))

print(outputs_sentence)

# 今天[天气|阳光|天|心情|空气]很好，我[想|要|打算|准备|就]去公园玩。

```


## 引用
Bibtex：
```tex
@techreport{zhuiyiwobert,
  title={WoBERT: Word-based Chinese BERT model - ZhuiyiAI},
  author={Jianlin Su},
  year={2020},
  url="https://github.com/ZhuiyiTechnology/WoBERT",
}
```

