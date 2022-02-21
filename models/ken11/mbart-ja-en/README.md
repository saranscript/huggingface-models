---
tags:
- translation
- japanese

language:
- ja
- en

license: mit

widget:
- text: "今日もご安全に"

---
## mbart-ja-en
このモデルは[facebook/mbart-large-cc25](https://huggingface.co/facebook/mbart-large-cc25)をベースに[JESC dataset](https://nlp.stanford.edu/projects/jesc/index_ja.html)でファインチューニングしたものです。  
This model is based on [facebook/mbart-large-cc25](https://huggingface.co/facebook/mbart-large-cc25) and fine-tuned with [JESC dataset](https://nlp.stanford.edu/projects/jesc/index_ja.html).

## How to use
```py
from transformers import (
    MBartForConditionalGeneration, MBartTokenizer
)

tokenizer = MBartTokenizer.from_pretrained("ken11/mbart-ja-en")
model = MBartForConditionalGeneration.from_pretrained("ken11/mbart-ja-en")

inputs = tokenizer("こんにちは", return_tensors="pt")
translated_tokens = model.generate(**inputs, decoder_start_token_id=tokenizer.lang_code_to_id["en_XX"], early_stopping=True, max_length=48)
pred = tokenizer.batch_decode(translated_tokens, skip_special_tokens=True)[0]
print(pred)
```

## Training Data
I used the [JESC dataset](https://nlp.stanford.edu/projects/jesc/index_ja.html) for training.  
Thank you for publishing such a large dataset.  

## Tokenizer
The tokenizer uses the [sentencepiece](https://github.com/google/sentencepiece) trained on the JESC dataset.

## Note
The result of evaluating the sacrebleu score for [JEC Basic Sentence Data of Kyoto University](https://nlp.ist.i.kyoto-u.ac.jp/EN/?JEC+Basic+Sentence+Data#i0163896) was `18.18` .

## Licenese
[The MIT license](https://opensource.org/licenses/MIT)
