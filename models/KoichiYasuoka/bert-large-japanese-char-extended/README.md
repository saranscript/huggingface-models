---
language:
- "ja"
tags:
- "japanese"
- "masked-lm"
- "wikipedia"
license: "cc-by-sa-4.0"
pipeline_tag: "fill-mask"
mask_token: "[MASK]"
widget:
- text: "酸素ボンベを充[MASK]する。"
---

# bert-large-japanese-char-extended

## Model Description

This is a BERT model pre-trained on Japanese Wikipedia texts, derived from [bert-large-japanese-char](https://huggingface.co/cl-tohoku/bert-large-japanese-char). Character-embeddings are enhanced to include all 常用漢字/人名用漢字 characters using [BertTokenizerFast](https://huggingface.co/transformers/model_doc/bert.html#berttokenizerfast). You can fine-tune `bert-large-japanese-char-extended` for downstream tasks, such as [POS-tagging](https://huggingface.co/KoichiYasuoka/bert-large-japanese-upos), dependency-parsing, and so on.

## How to Use

```py
from transformers import AutoTokenizer,AutoModelForMaskedLM
tokenizer=AutoTokenizer.from_pretrained("KoichiYasuoka/bert-large-japanese-char-extended")
model=AutoModelForMaskedLM.from_pretrained("KoichiYasuoka/bert-large-japanese-char-extended")
```

