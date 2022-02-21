---
language:
- nl
datasets:
- yhavinga/mc4_nl_cleaned
tags:
- seq2seq
- lm-head
license: apache-2.0
inference: false
---

# T5-base pre-trained on cleaned Dutch mC4 🇳🇱

A [T5](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) v1.1 base model pre-trained from scratch on [Dutch mC4](https://huggingface.co/datasets/yhavinga/mc4_nl_cleaned). This model achieves an evaluation accuracy of 0,78 and loss 0,96.

* Pre-trained T5 models need to be finetuned before they can be used for downstream tasks, therefore the inference widget on the right has been turned off.
* For a fine-tuned version for summarization, see [yhavinga/t5-v1.1-base-dutch-cnn-test](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cnn-test).
* For a demo of the Dutch CNN summarization models, head over to the Hugging Face Spaces for
the **[Netherformer 📰](https://huggingface.co/spaces/flax-community/netherformer)** example application!
* T5 paper: [Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer](https://arxiv.org/pdf/1910.10683.pdf)

![model image](https://camo.githubusercontent.com/623b4dea0b653f2ad3f36c71ebfe749a677ac0a1/68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f6d61782f343030362f312a44304a31674e51663876727255704b657944387750412e706e67)

## Tokenizer

* SentencePiece tokenizer trained from scratch for Dutch on mC4 nl cleaned with scripts from the Huggingface
  Transformers [Flax examples](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling).

## Dataset

All models listed below are trained on of the `full` configuration (39B tokens) of
[cleaned Dutch mC4](https://huggingface.co/datasets/yhavinga/mc4_nl_cleaned),
which is the original mC4, except

  * Documents that contained words from a selection of the Dutch and English [List of Dirty Naught Obscene and Otherwise Bad Words](https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words) are removed
  * Sentences with less than 3 words are removed
  * Sentences with a word of more than 1000 characters are removed
  * Documents with less than 5 sentences are removed
  * Documents with "javascript", "lorum ipsum", "terms of use", "privacy policy", "cookie policy", "uses cookies",
    "use of cookies", "use cookies", "elementen ontbreken", "deze printversie" are removed.
 
## Models

TL;DR: [yhavinga/t5-v1.1-base-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cased) is the best model.

* `yhavinga/t5-base-dutch` is a re-training of the Dutch T5 base v1.0 model trained during the summer 2021
  Flax/Jax community week. Accuracy was improved from 0.64 to 0.70.
* The two T5 v1.1 base models are an uncased and cased version of `t5-v1.1-base`, again pre-trained from scratch on Dutch,
  with a tokenizer also trained from scratch. The t5 v1.1 models are slightly different from the t5 models, and the 
  base models are trained with a dropout of 0.0. For fine-tuning it is intended to set this back to 0.1.
* The large cased model is a pre-trained Dutch version of `t5-v1.1-large`. Training of t5-v1.1-large proved difficult. 
  Without dropout regularization, the training would diverge at a certain point. With dropout training went better,
  be it much slower than training the t5-model. At some point convergance was too slow to warrant further training.
  The latest checkpoint, training scripts and metrics are available for reference. For actual fine-tuning the cased
  base model is probably the better choice.

|                                                                                                   | model   | train seq len | acc      | loss     | batch size | epochs | steps   | dropout | optim     | lr   | duration |
|---------------------------------------------------------------------------------------------------|---------|---------------|----------|----------|------------|--------|---------|---------|-----------|------|----------|
| [yhavinga/t5-base-dutch](https://huggingface.co/yhavinga/t5-base-dutch)                           | T5      | 512           | 0,70     | 1,38     | 128        | 1      | 528481  | 0.1     | adafactor | 5e-3 | 2d 9h    |
| [yhavinga/t5-v1.1-base-dutch-uncased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-uncased) | t5-v1.1 | 1024          | 0,73     | 1,20     | 64         | 2      | 1014525 | 0.0     | adafactor | 5e-3 | 5d 5h    |
| [yhavinga/t5-v1.1-base-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cased)     | t5-v1.1 | 1024          | **0,78** | **0,96** | 64         | 2      | 1210000 | 0.0     | adafactor | 5e-3 | 6d 6h    |
| [yhavinga/t5-v1.1-large-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-large-dutch-cased)   | t5-v1.1 | 512           | 0,76     | 1,07     | 64         | 1      | 1120000 | 0.1     | adafactor | 5e-3 | 86 13h   |

The cased t5-v1.1 Dutch models were fine-tuned on summarizing the CNN Daily Mail dataset.

|                                                                                                       | model   | input len | target len | Rouge1 | Rouge2 | RougeL | RougeLsum | Test Gen Len | epochs | batch size | steps | duration |
|-------------------------------------------------------------------------------------------------------|---------|-----------|------------|--------|--------|--------|-----------|--------------|--------|------------|-------|----------|
| [yhavinga/t5-v1.1-base-dutch-cnn-test](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cnn-test)   | t5-v1.1 | 1024      | 96         | 34,8   | 13,6   | 25,2   | 32,1      | 79           | 6      | 64         | 26916 | 2h 40m   |
| [yhavinga/t5-v1.1-large-dutch-cnn-test](https://huggingface.co/yhavinga/t5-v1.1-large-dutch-cnn-test) | t5-v1.1 | 1024      | 96         | 34,4   | 13,6   | 25,3   | 31,7      | 81           | 5      | 16         | 89720 | 11h      |


## Acknowledgements

This project would not have been possible without compute generously provided by Google through the
[TPU Research Cloud](https://sites.research.google/trc/). The HuggingFace 🤗 ecosystem was also
instrumental in many, if not all parts of the training. The following repositories where helpful in setting up the TPU-VM,
and training the models:

* [Gsarti's Pretrain and Fine-tune a T5 model with Flax on GCP](https://github.com/gsarti/t5-flax-gcp)
* [HUggingFace Flax MLM examples](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling)
* [Flax/Jax Community week t5-base-dutch](https://huggingface.co/flax-community/t5-base-dutch)

Created by [Yeb Havinga](https://www.linkedin.com/in/yeb-havinga-86530825/)