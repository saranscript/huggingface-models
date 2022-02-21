---
tags:
- generated_from_trainer
datasets:
- xsum
metrics:
- rouge
model-index:
- name: t5-small-finetuned_xsum
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: xsum
      type: xsum
      args: default
    metrics:
    - name: Rouge1
      type: rouge
      value: 33.1688
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned_xsum

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the xsum dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0881
- Rouge1: 33.1688
- Rouge2: 11.831
- Rougel: 26.796
- Rougelsum: 26.7931
- Gen Len: 18.7957

## Model description

More information needed

## Intended uses & limitations

The Extreme Summarization (XSum) dataset is a dataset for evaluation of abstractive single-document summarization systems. The goal is to create a short, one-sentence new summary answering the question “What is the article about?”. The dataset consists of 226,711 news articles accompanied with a one-sentence summary. The articles are collected from BBC articles (2010 to 2017) and cover a wide variety of domains (e.g., News, Politics, Sports, Weather, Business, Technology, Science, Health, Family, Education, Entertainment and Arts). The official random split contains 204,045 (90%), 11,332 (5%) and 11,334 (5) documents in training, validation and test sets, respectively.

T5, or Text-to-Text Transfer Transformer, is a Transformer based architecture that uses a text-to-text approach. Every task – including translation, question answering, and classification – is cast as feeding the model text as input and training it to generate some target text. This allows for the use of the same model, loss function, hyperparameters, etc. across our diverse set of tasks. The changes compared to BERT include:

-   adding a causal decoder to the bidirectional architecture.
-   replacing the fill-in-the-blank cloze task with a mix of alternative pre-training tasks.
 

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 50

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| 2.3789        | 1.0   | 12753  | 2.2274          | 31.3107 | 10.1407 | 25.0522 | 25.0423   | 18.8193 |
| 2.3565        | 2.0   | 25506  | 2.2159          | 31.5958 | 10.4022 | 25.3267 | 25.3228   | 18.7992 |
| 2.3504        | 3.0   | 38259  | 2.2037          | 31.8838 | 10.5974 | 25.5777 | 25.5786   | 18.7928 |
| 2.3345        | 4.0   | 51012  | 2.1956          | 31.8402 | 10.5656 | 25.5027 | 25.4994   | 18.8163 |
| 2.3175        | 5.0   | 63765  | 2.1868          | 31.9412 | 10.7187 | 25.6688 | 25.6719   | 18.7902 |
| 2.3177        | 6.0   | 76518  | 2.1805          | 31.9831 | 10.7074 | 25.6869 | 25.6863   | 18.8099 |
| 2.3027        | 7.0   | 89271  | 2.1734          | 32.0714 | 10.7714 | 25.7193 | 25.7141   | 18.7961 |
| 2.289         | 8.0   | 102024 | 2.1667          | 32.1598 | 10.883  | 25.8608 | 25.8605   | 18.8144 |
| 2.2875        | 9.0   | 114777 | 2.1622          | 32.0933 | 10.9046 | 25.8399 | 25.8329   | 18.8009 |
| 2.2796        | 10.0  | 127530 | 2.1547          | 32.391  | 11.112  | 26.0903 | 26.0931   | 18.7992 |
| 2.286         | 11.0  | 140283 | 2.1504          | 32.4479 | 11.1077 | 26.1274 | 26.1267   | 18.7975 |
| 2.2542        | 12.0  | 153036 | 2.1464          | 32.4059 | 11.1583 | 26.1111 | 26.1047   | 18.8042 |
| 2.2526        | 13.0  | 165789 | 2.1416          | 32.425  | 11.2178 | 26.1854 | 26.1795   | 18.7865 |
| 2.2374        | 14.0  | 178542 | 2.1372          | 32.299  | 11.1047 | 26.0495 | 26.0434   | 18.8016 |
| 2.2295        | 15.0  | 191295 | 2.1331          | 32.4283 | 11.2233 | 26.135  | 26.128    | 18.8004 |
| 2.2213        | 16.0  | 204048 | 2.1306          | 32.4948 | 11.2885 | 26.2607 | 26.2551   | 18.7854 |
| 2.1985        | 17.0  | 216801 | 2.1282          | 32.5872 | 11.3243 | 26.31   | 26.3062   | 18.7986 |
| 2.1993        | 18.0  | 229554 | 2.1245          | 32.6278 | 11.3196 | 26.3142 | 26.315    | 18.7809 |
| 2.2044        | 19.0  | 242307 | 2.1223          | 32.676  | 11.3871 | 26.356  | 26.3426   | 18.8007 |
| 2.2035        | 20.0  | 255060 | 2.1188          | 32.8736 | 11.4703 | 26.4901 | 26.4899   | 18.7863 |
| 2.1909        | 21.0  | 267813 | 2.1167          | 32.8288 | 11.4666 | 26.4992 | 26.4877   | 18.796  |
| 2.1835        | 22.0  | 280566 | 2.1141          | 32.9183 | 11.5267 | 26.5302 | 26.5338   | 18.8034 |
| 2.1845        | 23.0  | 293319 | 2.1127          | 32.7907 | 11.444  | 26.4614 | 26.459    | 18.8054 |
| 2.1725        | 24.0  | 306072 | 2.1109          | 32.8191 | 11.4973 | 26.5109 | 26.5012   | 18.7818 |
| 2.1805        | 25.0  | 318825 | 2.1082          | 32.7333 | 11.4325 | 26.4093 | 26.4028   | 18.7986 |
| 2.1661        | 26.0  | 331578 | 2.1063          | 32.8703 | 11.5443 | 26.5105 | 26.5101   | 18.7962 |
| 2.1606        | 27.0  | 344331 | 2.1048          | 32.884  | 11.558  | 26.5504 | 26.5465   | 18.7939 |
| 2.1508        | 28.0  | 357084 | 2.1032          | 32.9699 | 11.6036 | 26.6348 | 26.6266   | 18.7983 |
| 2.1479        | 29.0  | 369837 | 2.1019          | 32.8247 | 11.5812 | 26.5659 | 26.5595   | 18.7992 |
| 2.1363        | 30.0  | 382590 | 2.1019          | 32.9982 | 11.6801 | 26.6552 | 26.6497   | 18.797  |
| 2.1513        | 31.0  | 395343 | 2.0996          | 32.9903 | 11.6632 | 26.6579 | 26.6521   | 18.7911 |
| 2.1389        | 32.0  | 408096 | 2.0981          | 33.0195 | 11.7282 | 26.683  | 26.6757   | 18.7824 |
| 2.1421        | 33.0  | 420849 | 2.0968          | 32.9967 | 11.6949 | 26.6734 | 26.662    | 18.796  |
| 2.1545        | 34.0  | 433602 | 2.0954          | 33.0943 | 11.7329 | 26.7367 | 26.7295   | 18.7871 |
| 2.1459        | 35.0  | 446355 | 2.0949          | 33.1534 | 11.816  | 26.775  | 26.7716   | 18.7914 |
| 2.1364        | 36.0  | 459108 | 2.0933          | 33.0686 | 11.7418 | 26.7147 | 26.7066   | 18.7901 |
| 2.1194        | 37.0  | 471861 | 2.0928          | 33.1276 | 11.8268 | 26.7684 | 26.7626   | 18.802  |
| 2.1292        | 38.0  | 484614 | 2.0925          | 33.0462 | 11.7669 | 26.6798 | 26.6783   | 18.802  |
| 2.1317        | 39.0  | 497367 | 2.0913          | 33.1402 | 11.7889 | 26.7822 | 26.7824   | 18.7962 |
| 2.1176        | 40.0  | 510120 | 2.0907          | 33.1488 | 11.8001 | 26.7749 | 26.7615   | 18.7992 |
| 2.1318        | 41.0  | 522873 | 2.0899          | 33.0963 | 11.8162 | 26.7433 | 26.7325   | 18.7924 |
| 2.1052        | 42.0  | 535626 | 2.0899          | 33.0764 | 11.7624 | 26.7294 | 26.7238   | 18.7911 |
| 2.1267        | 43.0  | 548379 | 2.0891          | 33.1292 | 11.8029 | 26.7684 | 26.7693   | 18.7885 |
| 2.1211        | 44.0  | 561132 | 2.0894          | 33.09   | 11.7676 | 26.7418 | 26.7394   | 18.7853 |
| 2.1243        | 45.0  | 573885 | 2.0880          | 33.1449 | 11.7899 | 26.7725 | 26.7634   | 18.7946 |
| 2.0947        | 46.0  | 586638 | 2.0885          | 33.1548 | 11.8108 | 26.808  | 26.8003   | 18.7917 |
| 2.1246        | 47.0  | 599391 | 2.0881          | 33.148  | 11.8208 | 26.803  | 26.7961   | 18.7913 |
| 2.127         | 48.0  | 612144 | 2.0877          | 33.1935 | 11.8399 | 26.8209 | 26.8142   | 18.7925 |
| 2.1231        | 49.0  | 624897 | 2.0878          | 33.158  | 11.8159 | 26.7898 | 26.785    | 18.794  |
| 2.1296        | 50.0  | 637650 | 2.0881          | 33.1688 | 11.831  | 26.796  | 26.7931   | 18.7957 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.10.0+cu113
- Datasets 1.14.0
- Tokenizers 0.10.3
