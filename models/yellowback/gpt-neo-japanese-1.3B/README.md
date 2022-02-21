---
language:
- ja
tags:
- text generation
- pytorch
- causal-lm
- japanese
license: apache-2.0
datasets:
- oscar
- cc100
- wikipedia
---


# GPT-Neo 1.3B pre-trained model for Japanese

## Model Description

GPT2/GPT3 like model trained on Japanese.corpus.

## Training data

- cc100 ja
- oscar ja
- wikipedia ja

## How to use

```
from transformers import pipeline
>>> generator = pipeline('text-generation', model='yellowback/gpt-neo-japanese-1.3B')
>>> generator("こんばんは、徳川家康です。", do_sample=True, max_length=50, num_return_sequences=3)

[{'generated_text': 'こんばんは、徳川家康です。 世の中を見渡してみても、残念なことだけれども、まぎれもなく「世のなか...\n5月になりました、家康です。 ゴールデンウィークも終ってしまい、世間では'},
 {'generated_text': 'こんばんは、徳川家康です。さあ今日は昨晩から降り続いた雨は上がりましたが、まだまだ雨脚は強いですが、晴れるところは晴れて欲しいですね。昨日の夜は仕事だったので、今日の夕'},
 {'generated_text': 'こんばんは、徳川家康です。 今回は、『世界史再考──日本史再考』という本を書いたあと、『世界史再考──日本史再考』の6~8章'}]
```
