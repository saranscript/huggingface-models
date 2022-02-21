---
language:
    - bn
thumbnail:
tags:
    -
license: apache-2.0
datasets:
    - oscar
    - wikipedia
metrics:
    -
---

# [WIP] Albert Bengali - dev version

## Model description

For the moment, only the tokenizer is available. The tokenizer is based on [SentencePiece](https://github.com/google/sentencepiece) with Unigram language model segmentation algorithm.

Taking into account certain characteristics of the language, we chose that:

-   the tokenizer passes in lower case all the texts because the Bengali language is a monocameral scrip (no difference between capital and lower case);
-   the sentence pieces can't go beyond the boundary of a word because the words are spaced by white spaces in the Bengali language.

## Intended uses & limitations

This tokenizer is adapted to the Bengali language. You can use it to pre-train an Albert model on the Bengali language.

#### How to use

To tokenize:

```python
from transformers import AlbertTokenizer
tokenizer = AlbertTokenizer.from_pretrained('SaulLu/albert-bn-dev')
text = "পোকেমন  জাপানী ভিডিও গেম কোম্পানি নিনটেন্ডো কর্তৃক প্রকাশিত একটি মিডিয়া ফ্র‍্যাঞ্চাইজি।"
encoded_input = tokenizer(text, return_tensors='pt')
```

#### Limitations and bias

Provide examples of latent issues and potential remediations.

## Training data

The tokenizer was trained on a random subset of 4M sentences of Bengali Oscar and Bengali Wikipedia.

## Training procedure

### Tokenizer

The tokenizer was trained with the [SentencePiece](https://github.com/google/sentencepiece) on 8 x Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz with 16GB RAM and 36GB SWAP.

```
import sentencepiece as spm
config = {
    "input": "./dataset/oscar_bn.txt,./dataset/wikipedia_bn.txt",
    "input_format": "text",
    "model_type": "unigram",
    "vocab_size": 32000,
    "self_test_sample_size": 0,
    "character_coverage": 0.9995,
    "shuffle_input_sentence": true,
    "seed_sentencepiece_size": 1000000,
    "shrinking_factor": 0.75,
    "num_threads": 8,
    "num_sub_iterations": 2,
    "max_sentencepiece_length": 16,
    "max_sentence_length": 4192,
    "split_by_unicode_script": true,
    "split_by_number": true,
    "split_digits": true,
    "control_symbols": "[MASK]",
    "byte_fallback": false,
    "vocabulary_output_piece_score": true,
    "normalization_rule_name": "nmt_nfkc_cf",
    "add_dummy_prefix": true,
    "remove_extra_whitespaces": true,
    "hard_vocab_limit": true,
    "unk_id": 1,
    "bos_id": 2,
    "eos_id": 3,
    "pad_id": 0,
    "bos_piece": "[CLS]",
    "eos_piece": "[SEP]",
    "train_extremely_large_corpus": true,
    "split_by_whitespace": true,
    "model_prefix": "./spiece",
    "input_sentence_size": 4000000,
    "user_defined_symbols": "(,),-,.,–,£,।",
}
spm.SentencePieceTrainer.train(**config)
```

<!-- ## Eval results

### BibTeX entry and citation info

```bibtex
@inproceedings{...,
  year={2020}
}
``` -->
