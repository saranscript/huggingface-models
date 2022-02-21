---
language: ja
license: cc-by-sa-4.0
datasets:
- wikipedia
---

# BERT base Japanese (character-level tokenization with whole word masking, jawiki-20200831)

This pretrained model is almost the same as [cl-tohoku/bert-base-japanese-char-v2](https://huggingface.co/cl-tohoku/bert-base-japanese-char-v2) but do not need `fugashi` or `unidic_lite`.
The only difference is in `word_tokenzer_type` property (specify `basic` instead of `mecab`) in `tokenizer_config.json`.
