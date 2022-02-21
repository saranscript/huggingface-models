---
language:
- dv
license: apache-2.0
---

# BERT base for Dhivehi

Pretrained model on Dhivehi language using masked language modeling (MLM).

## Tokenizer

The *WordPiece* tokenizer uses several components:

* **Normalization**: lowercase and then NFKD unicode normalization.
* **Pretokenization**: splits by whitespace and punctuation.
* **Postprocessing**: single sentences are output in format `[CLS] sentence A [SEP]` and pair sentences in format `[CLS] sentence A [SEP] sentence B [SEP]`.

## Training

Training was performed over 16M+ Dhivehi sentences/paragraphs put together by [@ashraq](https://huggingface.co/ashraq). An Adam optimizer with weighted decay was used with following parameters:

* Learning rate: 1e-5
* Weight decay: 0.1
* Warmup steps: 10% of data
