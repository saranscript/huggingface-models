---
tags:
- ner
- token-classification
- japanese
- bert

language:
- ja

license: mit

---
## bert-japanese-ner
このモデルは日本語の固有表現抽出タスクを目的として、[京都大学 黒橋・褚・村脇研究室が公開しているBERT日本語Pretrainedモデル](https://nlp.ist.i.kyoto-u.ac.jp/?ku_bert_japanese)をベースに[ストックマーク株式会社が公開しているner-wikipedia-dataset](https://github.com/stockmarkteam/ner-wikipedia-dataset)でファインチューニングしたものです。  

## How to use
このモデルはTokenizerに上述の京都大学BERT日本語PretrainedモデルのTokenizerを利用します。  
当リポジトリにTokenizerは含まれていません。  
利用する際は別途ダウンロードしてご用意ください。  
  
また、Tokenizerとは別に[Juman++](https://nlp.ist.i.kyoto-u.ac.jp/?JUMAN%2B%2B)と[pyknp](https://nlp.ist.i.kyoto-u.ac.jp/?PyKNP)を利用します。  
予めインストールしておいてください。
```py
from transformers import (
    BertForTokenClassification, BertTokenizer
)

from pyknp import Juman


jumanpp = Juman()
tokenizer = BertTokenizer.from_pretrained("ダウンロードした京都大学のTokenizerのファイルパス")

model = BertForTokenClassification.from_pretrained("ken11/bert-japanese-ner")

text = "なにか文章"
juman_result = jumanpp.analysis(text)
tokenized_text = [mrph.midasi for mrph in juman_result.mrph_list()]
inputs = tokenizer(tokenized_text, return_tensors="pt", padding='max_length', truncation=True, max_length=64, is_split_into_words=True)
pred = model(**inputs).logits[0]
pred = np.argmax(pred.detach().numpy(), axis=-1)
labels = []
for i, label in enumerate(pred):
    if i + 1 > len(tokenized_text):
        continue
    labels.append(model.config.id2label[label])
    print(f"{tokenized_text[i]}: {model.config.id2label[label]}")
print(tokenized_text)
print(labels)
```

## Training Data
学習には[ストックマーク株式会社が公開しているner-wikipedia-dataset](https://github.com/stockmarkteam/ner-wikipedia-dataset)を利用しました。  
便利なデータセットを公開していただきありがとうございます。

## Note
固有表現抽出のラベルは学習データセットのものをBILUO形式に変換して使用しています。  
ラベルの詳細については[ner-wikipedia-datasetの概要](https://github.com/stockmarkteam/ner-wikipedia-dataset#%E6%A6%82%E8%A6%81)をご確認ください。

## Licenese
[The MIT license](https://opensource.org/licenses/MIT)
