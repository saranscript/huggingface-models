---
language: ja
tags:
- mobilebert
license: cc-by-sa-3.0
datasets:
- wikipedia
---

# MobileBERT 日本語事前学習済みモデル爆誕！！
AI関係の仕事をしている櫻本です。  
2020年に発表されたBERTの発展型モデルの一つである「MobileBERT」の、日本語事前学習済みモデルを構築しました。  
このページを見つけた方はかなりラッキーですから、ぜひ一度使ってみてください！！  
BERTの推論速度の遅さを嘆いている方にお薦めです。

# 利用方法
既にtransformersでBERTを利用されている方向けの説明です。  
トークナイザは東北大学さんのモデル(cl-tohoku/bert-large-japanese)からお借りしましたのでご指定ください。  
後は、**BertFor**なんちゃら～のクラスを**MobileBertFor**なんちゃら～に直して、このリポジトリを指定するだけです！  
```from transformers import BertJapaneseTokenizer, MobileBertForSequenceClassification
tokenizer = BertJapaneseTokenizer.from_pretrained("cl-tohoku/bert-large-japanese")
model = MobileBertForSequenceClassification.from_pretrained("ysakuramoto/mobilebert-ja") # 文書分類の場合
```
(注意：文書分類などのタスクに利用するには、ファインチューニングが必要です)  

# BERTとの性能比較
文書分類と固有表現抽出について、ファインチューニング・性能評価を行いました。  
参考程度にご覧ください。(ファインチューニング後の性能を保証するものではありません)

  - 文書分類(MobileBertForSequenceClassification)
  |メトリック|BERT|MobileBERT(高速化前)|MobileBERT(高速化後)|
  |-----------|-----------| ------- | -------- |
  |学習時間(s)|585.0|399.7|-|
  |推論時間(s)|259.0|108.7|70.5|
  |精度|86.4%|85.5%|86.4%|
  |モデルファイルサイズ(MB)|440.2|-|41.8|
  
    - 条件
      - ライブドアニュースコーパスのタイトルとカテゴリで学習・推論。
      - 比較対象のBERTモデルは東北大学さんの"cl-tohoku/bert-base-japanese-whole-word-masking"。
      - 推論データ n=1,474。精度はAccuracy
      - 学習パラメータ: エポック数=10, lr=1e-4
      - 推論時の高速化として、枝刈り(-20%)・量子化・jitコンパイルを実施。
      - Google Colabにて、学習にGPU、推論にCPUを利用。バッチ処理でなく1件ずつ推論。
      - それぞれ、学習～推論を3回実施した平均値。
  
  - 固有表現抽出(MobileBertForTokenClassification)
  |メトリック|BERT|MobileBERT(高速化前)|MobileBERT(高速化後)|
  |-----------|-----------| ------- | -------- |
  |学習時間(s)|428.0|294.0|-|
  |推論時間(s)|163.5|78.4|40.9|
  |精度|86.4%|82.5%|83.3%|
  |モデルファイルサイズ(MB)|440.2|-|41.8|
    
    - 条件
      - ストックマーク社さんのwikipediaデータセットで学習・推論。(https://github.com/stockmarkteam/ner-wikipedia-dataset)  
      - 比較対象のBERTモデルは東北大学さんの"cl-tohoku/bert-base-japanese-whole-word-masking"。
      - 推論データ n=2,140。精度は完全一致のf-measure
      - 学習パラメータ: エポック数=10, lr=1e-4
      - 推論時の高速化として、枝刈り(-20%)・量子化・jitコンパイルを実施。
      - Google Colabにて、学習にGPU、推論にCPUを利用。バッチ処理でなく1件ずつ推論。
      - それぞれ、学習～推論を3回実施した平均値。

# モデルの説明
- モデルの構造
  - 論文中の"MobileBERT"構造に従いました。(論文中にはMobileBERT<sub>TINY</sub>というバージョンもありますがそちらではないです) 
    - 論文中のTable.1 をご確認ください。 https://arxiv.org/abs/2004.02984
- 学習に利用したデータ
  - 東北大学さんが公開されている方法で、2021年8月時点のwikipediaデータを加工・利用しました。
    - 東北大学さんのgithub https://github.com/cl-tohoku/bert-japanese
- トークナイザ
  - 東北大学さんのモデル"cl-tohoku/bert-large-japanese"からお借りしました。vocab sizeは32,768です。
- 学習方法
  - Google ColabからTPUを用いて学習しました。
    1. IB-BERT<sub>LARGE</sub>をlr=5e-4で1Mステップ学習しました。
    1. IB-BERT<sub>LARGE</sub>を240kステップ蒸留後、mobileBERTをlr=5e-4で2Mステップ学習しました。
  - トータルで2ヶ月半くらいかかりました。。エラー出まくってつらかったです。
  
# ライセンス
[CC-BY SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/deed.ja)  
トークナイザについては東北大学さんのモデル"cl-tohoku/bert-large-japanese"からお借りしました。

# 免責
このモデルを利用・参照することで発生したあらゆる不都合や損害について、一切の責任を負いかねます。