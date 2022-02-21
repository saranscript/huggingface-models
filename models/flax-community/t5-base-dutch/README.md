---
language: 
- dutch
tags:
- seq2seq
- lm-head
datasets:
- yhavinga/mc4_nl_cleaned
license: apache-2.0
inference: false
---

# t5-base-dutch 

Created by [Yeb Havinga](https://www.linkedin.com/in/yeb-havinga-86530825/)
& [Dat Nguyen](https://www.linkedin.com/in/dat-nguyen-49a641138/) during the [Hugging Face community week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organized by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google, for the project [Pre-train T5 from scratch in Dutch](https://discuss.huggingface.co/t/pretrain-t5-from-scratch-in-dutch/8109).

See also the fine-tuned [t5-base-dutch-demo](https://huggingface.co/flax-community/t5-base-dutch-demo) model,
and the demo application **[Netherformer 📰](https://huggingface.co/spaces/flax-community/netherformer)**,
that are based on this model.

**5 jan 2022: Model updated. Evaluation accuracy increased from 0.64 to 0.70.**

**11 jan 2022: See also [yhavinga/t5-v1.1-base-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cased) with eval acc 0.78**

## Model

* Configuration based on `google/t5-base`
* 12 layers, 12 heads
* Dropout set to 0.1

## Dataset

This model was trained on the `full` configuration of [cleaned Dutch mC4](https://huggingface.co/datasets/yhavinga/mc4_nl_cleaned),
which is the original mC4, except

  * Documents that contained words from a selection of the Dutch and English [List of Dirty Naught Obscene and Otherwise Bad Words](https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words) are removed
  * Sentences with less than 3 words are removed
  * Sentences with a word of more than 1000 characters are removed
  * Documents with less than 5 sentences are removed
  * Documents with "javascript", "lorum ipsum", "terms of use", "privacy policy", "cookie policy", "uses cookies",
    "use of cookies", "use cookies", "elementen ontbreken", "deze printversie" are removed.

## Tokenization

A SentencePiece tokenizer was trained from scratch on this dataset.
The total tokens of the `full` configuration is 34B 

## Training

The model was trained on the `full` mc4_nl_cleaned dataset configuration for 1 epoch, consisting of 34B tokens,
for 528 482 steps with a batch size of 128 and took 57 hours.
A triangle learning rate schedule was used, with peak learning rate 0.005.

## Evaluation

* Loss: 1.38
* Accuracy: 0.70
