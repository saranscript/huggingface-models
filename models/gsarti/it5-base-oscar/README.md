---
language:
- it
datasets:
- oscar
tags:
 - seq2seq
 - lm-head
license: apache-2.0
inference: false
---

# Italian T5 Base (Oscar) 🇮🇹

*This repository contains the model formerly known as `gsarti/t5-base-it`* 

The [IT5](https://huggingface.co/models?search=it5) model family represents the first effort in pretraining large-scale sequence-to-sequence transformer models for the Italian language, following the approach adopted by the original [T5 model](https://github.com/google-research/text-to-text-transfer-transformer). 

This model is released as part of the project ["IT5: Large-Scale Text-to-Text Pretraining for Italian Language Understanding and Generation"](https://gsarti.com) (to be released), by [Gabriele Sarti](https://gsarti.com/) with the support of [Huggingface](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) and with TPU usage sponsored by Google's [TPU Research Cloud](https://sites.research.google/trc/). All the training was conducted on a single TPU3v8-VM machine on Google Cloud. Refer to the Tensorboard tab of the repository for an overview of the training process.

*The inference widget is deactivated because the model needs a task-specific seq2seq fine-tuning on a downstream task to be useful in practice. The model [`gsarti/it5-base-nli`](https://huggingface.co/gsarti/it5-base-nli) provides an example of this model fine-tuned on a downstream NLI task.*

## Model variants

This repository contains the checkpoints for a `base` version of the model trained on the [OSCAR corpus](https://oscar-corpus.com/) using 🤗 Datasets. The original configuration for the model `t5-base` was adopted, with the exception of the parameter `dropout_rate` that was set at `0` instead of `0.1` during pre-training, following the implementation of [`t5-v1.1`](https://huggingface.co/google/t5-v1_1-base). The tokenizer is a `SentencePieceUnigramTokenizer` trained on the first 2M sentences of the Italian portion of the [`mC4`](https://huggingface.co/datasets/mc4) corpus. An improved version of the model trained on the [Thoroughly Cleaned Italian mC4 Corpus](https://huggingface.co/datasets/gsarti/clean_mc4_it) (~41B words, ~275GB) is also available under the name [`gsarti/it5-base`](https://huggingface.co/gsarti/it5-base). The training procedure is made available [on Github](https://github.com/gsarti/t5-flax-gcp).

The following table summarizes the parameters for all available models

|                       |`it5-small`            |`it5-base`            |`it5-large`            |`it5-base-oscar` (this one)       |
|-----------------------|-----------------------|----------------------|-----------------------|----------------------------------|
|`dataset`              |`gsarti/clean_mc4_it`  |`gsarti/clean_mc4_it` |`gsarti/clean_mc4_it`  |`oscar/unshuffled_deduplicated_it`|
|`architecture`         |`google/t5-v1_1-small` |`google/t5-v1_1-base` |`google/t5-v1_1-large` |`t5-base`                         |
|`learning rate`        | 5e-3                  | 5e-3                 | 5e-3                  | 1e-2                             |
|`steps`                | 1'050'000             | 1'050'000            | 2'100'000             | 258'000                          |
|`training time`        | 36 hours              | 101 hours            | 370 hours             | 98 hours                         |
|`ff projection`        |`gated-gelu`           |`gated-gelu`          |`gated-gelu`           |`relu`                            |
|`tie embeds`           |`false`                |`false`               |`false`                |`true`                            |
|`optimizer`            | adafactor             | adafactor            | adafactor             | adafactor                        |
|`max seq. length`      | 512                   | 512                  | 512                   | 512                              |
|`per-device batch size`| 16                    | 16                   | 8                     | 16                               |
|`tot. batch size`      | 128                   | 128                  | 64                    | 128                              |
|`weigth decay`         | 1e-3                  | 1e-3                 | 1e-2                  | 1e-3                             |
|`validation split size`| 15K examples          | 15K examples         | 15K examples          | 15K examples                     |

The high training time of `it5-base-oscar` was due to [a bug](https://github.com/huggingface/transformers/pull/13012) in the training script.

For a list of individual model parameters, refer to the `config.json` file in the respective repositories.

## Using the models

```python
from transformers import T5Tokenizer, T5ForConditionalGeneration

tokenizer = T5Tokenizer.from_pretrained("gsarti/it5-base-oscar")
model = T5ForConditionalGeneration.from_pretrained("gsarti/it5-base-oscar")
```

*Note: You will need to fine-tune the model on your downstream seq2seq task to use it. See an example [here](https://huggingface.co/gsarti/it5-base-nli).*

Flax and Tensorflow versions of the model are also available:

```python
from transformers import FlaxT5ForConditionalGeneration, TFT5ForConditionalGeneration

model_flax = FlaxT5ForConditionalGeneration.from_pretrained("gsarti/it5-base-oscar")
model_tf = TFT5ForConditionalGeneration.from_pretrained("gsarti/it5-base-oscar")
```

## Limitations

Due to the nature of the web-scraped corpus on which IT5 models were trained, it is likely that their usage could reproduce and amplify pre-existing biases in the data, resulting in potentially harmful content such as racial or gender stereotypes and conspiracist views. For this reason, the study of such biases is explicitly encouraged, and model usage should ideally be restricted to research-oriented and non-user-facing endeavors.

## Model curators

For problems or updates on this model, please contact [gabriele.sarti996@gmail.com](mailto:gabriele.sarti996@gmail.com).

##  Citation Information

*Coming soon!*