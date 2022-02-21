---
language: yue
license: apache-2.0
metrics:
- DRCD
- openrice-senti
- lihkg-cat
- wordshk-sem
---

# XLNet Hongkongese Base

## Model description

XLNet trained exclusively with data from Hong Kong. A signaficant amount of Hongkongese/Cantonese/Yue is included in the training data.

## Intended uses & limitations

This model is an alternative to Chinese models. It may offer better performance for tasks catering to the langauge usage of Hong Kongers. Yue Wikipedia is used which is much smaller than Chinese Wikipedia; this model will lack the breath of knowledge compared to other Chinese models.

#### How to use

This is the base model trained from the official repo. Further finetuning will be needed for use on downstream tasks. It can also be used to generate text.

#### Limitations and bias

The training data consists of mostly news articles and blogs. There is probably a bias towards formal language usage. 

For text generation, like other XLNet models, a longer context will help generate better text. Overall result is not as good as GPT-2.

## Training data

The following is the list of data sources. Total characters is about 507M.

| Data                                              |   % |
| ------------------------------------------------- | --: |
| News Articles / Blogs                             | 58% |
| Yue Wikipedia / EVCHK                             | 18% |
| Restaurant Reviews                                | 12% |
| Forum Threads                                     | 12% |
| Online Fiction                                    |  1% |

The following is the distribution of different languages within the corpus.

| Language                                          |   % |
| ------------------------------------------------- | --: |
| Standard Chinese                                  | 62% |
| Hongkongese                                       | 30% |
| English                                           |  8% |

## Training procedure

Model was trained on a single TPUv3 from the official repo with the default parameters.

| Parameter                                        | Value |
| ------------------------------------------------ | ----: |
| Batch Size                                       | 32    |
| Max Sequence Size                                | 512   |
| Vocab Size                                       | 32000 |

 *Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC)*

## Eval results

Average evaluation task results over 10 runs. Comparison using the original repo model and code. Chinese models are available from [Joint Laboratory of HIT and iFLYTEK Research (HFL)](https://huggingface.co/hfl)

| Model       | DRCD (EM/F1) | openrice-senti | lihkg-cat | wordshk-sem |
|:-----------:|:------------:|:--------------:|:---------:|:-----------:|
| Chinese     | 82.8 / 91.8  | 79.8           | 70.7      | 72.0 / 78.9*|
| Hongkongese | 76.1 / 76.1  | 81.4           | 69.5      | 66.7 / 87.3*|

\* With the default of 3 epoches, 6 of 10 Chinese finetuned models have accuracy of 66.7 (always negative baseline). All Hongkongese finetuned models have accuracy of 66.7. The \* values are the accuracy after 24 epoches.