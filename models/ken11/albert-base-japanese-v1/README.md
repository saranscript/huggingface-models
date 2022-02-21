---
tags:
- fill-mask
- japanese
- albert

language:
- ja

license: mit

widget:
- text: "2022年の[MASK]概要"

---
## albert-base-japanese-v1
日本語事前学習済みALBERTモデルです  

## How to use
### ファインチューニング
このモデルはPreTrainedモデルです  
基本的には各種タスク用にファインチューニングして使用されることを想定しています  

### Fill-Mask
このモデルではTokenizerにSentencepieceを利用しています  
そのままでは`[MASK]`トークンのあとに[余計なトークンが混入する問題](https://ken11.jp/blog/sentencepiece-tokenizer-bug)があるので、利用する際には以下のようにする必要があります  
#### for PyTorch
```py
from transformers import (
    AlbertForMaskedLM, AlbertTokenizerFast
)
import torch


tokenizer = AlbertTokenizerFast.from_pretrained("ken11/albert-base-japanese-v1")
model = AlbertForMaskedLM.from_pretrained("ken11/albert-base-japanese-v1")

text = "大学で[MASK]の研究をしています"
tokenized_text = tokenizer.tokenize(text)
del tokenized_text[tokenized_text.index(tokenizer.mask_token) + 1]

input_ids = [tokenizer.cls_token_id]
input_ids.extend(tokenizer.convert_tokens_to_ids(tokenized_text))
input_ids.append(tokenizer.sep_token_id)

inputs = {"input_ids": [input_ids], "token_type_ids": [[0]*len(input_ids)], "attention_mask": [[1]*len(input_ids)]}
batch = {k: torch.tensor(v, dtype=torch.int64) for k, v in inputs.items()}
output = model(**batch)[0]
_, result = output[0, input_ids.index(tokenizer.mask_token_id)].topk(5)

print(tokenizer.convert_ids_to_tokens(result.tolist()))
# ['英語', '心理学', '数学', '医学', '日本語']
```

#### for TensorFlow
```py
from transformers import (
    TFAlbertForMaskedLM, AlbertTokenizerFast
)
import tensorflow as tf


tokenizer = AlbertTokenizerFast.from_pretrained("ken11/albert-base-japanese-v1")
model = TFAlbertForMaskedLM.from_pretrained("ken11/albert-base-japanese-v1")

text = "大学で[MASK]の研究をしています"
tokenized_text = tokenizer.tokenize(text)
del tokenized_text[tokenized_text.index(tokenizer.mask_token) + 1]

input_ids = [tokenizer.cls_token_id]
input_ids.extend(tokenizer.convert_tokens_to_ids(tokenized_text))
input_ids.append(tokenizer.sep_token_id)

inputs = {"input_ids": [input_ids], "token_type_ids": [[0]*len(input_ids)], "attention_mask": [[1]*len(input_ids)]}
batch = {k: tf.convert_to_tensor(v, dtype=tf.int32) for k, v in inputs.items()}
output = model(**batch)[0]
result = tf.math.top_k(output[0, input_ids.index(tokenizer.mask_token_id)], k=5)

print(tokenizer.convert_ids_to_tokens(result.indices.numpy()))
# ['英語', '心理学', '数学', '医学', '日本語']
```

## Training Data
学習には
- [日本語Wikipediaの全文](https://ja.wikipedia.org/wiki/Wikipedia:%E3%83%87%E3%83%BC%E3%82%BF%E3%83%99%E3%83%BC%E3%82%B9%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89)
- [livedoorニュースコーパス](https://www.rondhuit.com/download.html#ldcc)

を利用しています  

## Tokenizer
トークナイザーは[Sentencepiece](https://github.com/google/sentencepiece)を利用しています  
こちらも学習データは同様です

## Licenese
[The MIT license](https://opensource.org/licenses/MIT)
