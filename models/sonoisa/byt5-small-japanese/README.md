---
language: ja
tags:
- byt5
- t5
- text2text-generation
- seq2seq
license: cc-by-sa-4.0
datasets:
- wikipedia
- oscar
- cc100
---

# 日本語ByT5事前学習済みモデル

This is a [ByT5 (a tokenizer-free extension of the Text-to-Text Transfer Transformer)](https://github.com/google-research/byt5/) model pretrained on Japanese corpus.

次の日本語コーパス（約100GB）を用いて事前学習を行ったByT5 (a tokenizer-free extension of the Text-to-Text Transfer Transformer) モデルです。  

* [Wikipedia](https://ja.wikipedia.org)の日本語ダンプデータ (2020年7月6日時点のもの)
* [OSCAR](https://oscar-corpus.com)の日本語コーパス
* [CC-100](http://data.statmt.org/cc-100/)の日本語コーパス

このモデルは事前学習のみを行なったものであり、特定のタスクに利用するにはファインチューニングする必要があります。  
本モデルにも、大規模コーパスを用いた言語モデルにつきまとう、学習データの内容の偏りに由来する偏った（倫理的ではなかったり、有害だったり、バイアスがあったりする）出力結果になる問題が潜在的にあります。
この問題が発生しうることを想定した上で、被害が発生しない用途にのみ利用するよう気をつけてください。


# 転移学習のサンプルコード

準備中


# ベンチマーク

livedoorニュースコーパスを用いたニュース記事のジャンル予測タスクの精度は次の通りです。

日本語T5 ([byt5-small-japanese](https://huggingface.co/sonoisa/byt5-small-japanese), パラメータ数は299M)

| label       |  precision  |  recall | f1-score | support |
| ----------- | ----------- | ------- | -------- | ------- |
|           0 |      0.94   |   0.89  |    0.91  |     130 |
|           1 |      0.93   |   0.94  |    0.93  |     121 |
|           2 |      0.88   |   0.93  |    0.90  |     123 |
|           3 |      0.90   |   0.87  |    0.88  |      82 |
|           4 |      0.95   |   0.95  |    0.95  |     129 |
|           5 |      0.94   |   0.95  |    0.94  |     141 |
|           6 |      0.98   |   0.96  |    0.97  |     127 |
|           7 |      0.98   |   0.98  |    0.98  |     127 |
|           8 |      0.97   |   0.97  |    0.97  |     120 |
|   accuracy  |             |         |    0.94  |    1100 |
|  macro avg  |      0.94   |   0.94  |    0.94  |    1100 |
| weighted avg |     0.94   |   0.94  |    0.94  |    1100 |


比較対象: 多言語T5 ([google/byt5-small](https://huggingface.co/google/byt5-small), パラメータ数は299M)

| label       |  precision  |  recall | f1-score | support |
| ----------- | ----------- | ------- | -------- | ------- |
|           0 |      0.93   |   0.88  |    0.91  |     130 |
|           1 |      0.90   |   0.79  |    0.84  |     121 |
|           2 |      0.75   |   0.86  |    0.80  |     123 |
|           3 |      0.87   |   0.79  |    0.83  |      82 |
|           4 |      0.93   |   0.96  |    0.94  |     129 |
|           5 |      0.87   |   0.95  |    0.91  |     141 |
|           6 |      0.98   |   0.93  |    0.96  |     127 |
|           7 |      0.97   |   0.91  |    0.94  |     127 |
|           8 |      0.89   |   0.94  |    0.91  |     120 |
|   accuracy  |             |         |    0.90  |    1100 |
|  macro avg  |      0.90   |   0.89  |    0.89  |    1100 |
| weighted avg |     0.90   |   0.90  |    0.90  |    1100 |


## 免責事項

本モデルの作者は本モデルを作成するにあたって、その内容、機能等について細心の注意を払っておりますが、モデルの出力が正確であるかどうか、安全なものであるか等について保証をするものではなく、何らの責任を負うものではありません。本モデルの利用により、万一、利用者に何らかの不都合や損害が発生したとしても、モデルやデータセットの作者や作者の所属組織は何らの責任を負うものではありません。利用者には本モデルやデータセットの作者や所属組織が責任を負わないことを明確にする義務があります。


## ライセンス

[CC-BY SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.ja)

[Common Crawlの利用規約](http://commoncrawl.org/terms-of-use/)も守るようご注意ください。
