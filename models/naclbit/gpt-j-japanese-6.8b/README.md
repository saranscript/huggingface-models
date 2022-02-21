---
language: 
  - ja
tags:
- japanese
- text-generation
- gptj
- pytorch
- transformers
- t5tokenizer
- sentencepiece
license: apache-2.0
---

This pre-trained model is work in progress! Model weight download will be available in the future.

A 6.8 billion parameter pre-trained model for Japanese language, based on EleutherAI's Mesh Transformer JAX, that has a similar model structure to their GPT-J-6B pre-trained model.

EleutherAIによるMesh Transformer JAXをコードベースとした、GPT-J-6Bに似たストラクチャと約68.7億パラメータを持つ日本語pre-trainedモデルです。

- We used T5Tokenizer and SentencePiece instead of GPT-2/3 tokenizer. Normalization done by SentencePiece is must for Japanese tokenizing as there are so much many more variations for common symbols than Western languages.
- Tokenizer has a vocabulary of 52,500 tokens and trained on Japanese Wikipedia dump as of 01 Aug 2021.
- The model fits within 16GB VRAM GPUs like P100 for inference up to 1688 context length. Full 2048 context length output requires 20GB VRAM or more (e.g. GTX3090/A5000).
- The model was trained with TPUv3-128 generously provided by Google TRC for about 4 weeks. We are currently formatting additional datasets and preparing for more training time.

## Specifications

| Hyperparameter    | Value  |
|-------------------|--------|
| n_parameters      | 6,876,450,080 |
| n_layers          | 32 |
| d_model           | 4,096  |
| d_ff              | 16,384 |
| n_heads           | 16     |
| d_head            | 256    |
| n_ctx             | 2,048  |
| n_vocab           | 52,512 |
| position encoding | [Rotary position encodings (RoPE)](https://arxiv.org/abs/2104.09864) |
| RoPE dimensions   | 64 |

## Instructions

We recommend to use finetuneanon's forked transformer codebase for inferencing as split checkpoint loads up a lot faster than monolithic checkpoint supported by HuggingFace Transformers repository.

The tokenizer still uses 50256 as the <|endoftext|> substitute. Therefore 50256 should be excluded when inferencing.

## Datasets

Lack of quality Japanese corpus was one of the major challenges when we trained the model. We aimed to compile well-formatted corpuses outside of Common Crawl.

The dataset is normalized and sanitized against leading and trailing spaces, excessive CR/LF repetitions.

The whole dataset is about 400GB (as of October 2021) and 106B tokens (compared to 825GB/300B tokens for The Pile).

** Common Crawl
- Jan-Dec 2018 72GB CC100-Japanese (https://metatext.io/datasets/cc100-japanese)
- November 2018 106GB OSCAR-Japanese (https://oscar-corpus.com)
- 75GB Converted 860GB Google C4 Multilingual Japanese (re-formatted)

** Books
- 140GB Web Fictions, non-fictions and blogs corpus
- 5GB Books and Aozora Bunko corpus (weighted 2x)

** News
- 1GB Scientific news, medical news and web news corpus

** Wikipedia
- Aug 2021 3GB Assorted and Deduplicated Japanese Wikipedia (weighted 2x)
- Aug 2021 Wikibooks, Wikinews, Wikiquote, Wikisource, Wiktionary, Wikiversity and Wikivoyage

** Other Corpuses
- 2018 OpenSubtitles (https://opus.nlpl.eu/OpenSubtitles-v2018.php)
- 80-90's BBS Logs
- Assorted Blogs Crawl
- QED-ja
- TED 2020-ja