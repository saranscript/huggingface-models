---
language: yue
license: apache-2.0
metrics:
- DRCD
- openrice-senti
- lihkg-cat
- wordshk-sem
---

# ELECTRA Hongkongese Large

## Model description

ELECTRA trained exclusively with data from Hong Kong. A signaficant amount of Hongkongese/Cantonese/Yue is included in the training data.

## Intended uses & limitations

This model is an alternative to Chinese models. It may offer better performance for tasks catering to the langauge usage of Hong Kongers. Yue Wikipedia is used which is much smaller than Chinese Wikipedia; this model will lack the breath of knowledge compared to other Chinese models.

#### How to use

This is the large model trained from the official repo. Further finetuning will be needed for use on downstream tasks. Other model sizes are also available.

#### Limitations and bias

The training data consists of mostly news articles and blogs. There is probably a bias towards formal language usage. 

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
| Batch Size                                       | 96    |
| Max Sequence Size                                | 512   |
| Mask Prob                                        | 0.25  |
| Learning Rate                                    | 2e-4  |
| Vocab Size                                       | 30000 |

 *Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC)*

## Eval results

Average evaluation task results over 10 runs. Comparison using the original repo model and code. Chinese models are available from [Joint Laboratory of HIT and iFLYTEK Research (HFL)](https://huggingface.co/hfl)

| Model       | DRCD (EM/F1) | openrice-senti | lihkg-cat | wordshk-sem |
|:-----------:|:------------:|:--------------:|:---------:|:-----------:|
| Chinese     | 88.8 / 93.6  | 79.8           | 70.4      | 90.4        |
| Hongkongese | 84.7 / 90.9  | 79.7           | 69.9      | 91.5        |
