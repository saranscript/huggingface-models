---
language: zh
widget:
- text: "今天是下雨天"
- text: "走向森林"
---

<h1 align="center">
CPM
</h1>


CPM(Chinese Pre-Trained Language Models), which has 2.6B parameters, made by the research team of Beijing Zhiyuan Institute of artificial intelligence and Tsinghua University @TsinghuaAI.

[repo: CPM-Generate](https://github.com/TsinghuaAI/CPM-Generate)

The One Thing You Need to Know is this model is not uploaded by official, the conver script is [here](https://github.com/mymusise/CPM-TF2Transformer/blob/main/transfor_CMP.ipynb)

# Overview

- **Language model**: CPM
- **Model size**: 2.6B parameters
- **Language**: Chinese

# How to use

How to use this model directly from the 🤗/transformers library:

```python
from transformers import XLNetTokenizer, TFGPT2LMHeadModel
import jieba

# add spicel process 
class XLNetTokenizer(XLNetTokenizer):
    translator = str.maketrans(" \n", "\u2582\u2583")

    def _tokenize(self, text, *args, **kwargs):
        text = [x.translate(self.translator) for x in jieba.cut(text, cut_all=False)]
        text = " ".join(text)
        return super()._tokenize(text, *args, **kwargs)

    def _decode(self, *args, **kwargs):
        text = super()._decode(*args, **kwargs)
        text = text.replace(' ', '').replace('\u2582', ' ').replace('\u2583', '\n')
        return text


tokenizer = XLNetTokenizer.from_pretrained('mymusise/CPM-GPT2-FP16')
model = TFGPT2LMHeadModel.from_pretrained("mymusise/CPM-GPT2-FP16")
```

How to generate text

```python
from transformers import TextGenerationPipeline


text_generater = TextGenerationPipeline(model, tokenizer)

texts = [
    '今天天气不错',
    '天下武功, 唯快不',
    """
    我们在火星上发现了大量的神奇物种。有神奇的海星兽，身上是粉色的，有5条腿；有胆小的猫猫兽，橘色，有4条腿；有令人恐惧的蜈蚣兽，全身漆黑，36条腿；有纯洁的天使兽，全身洁白无瑕，有3条腿；有贪吃的汪汪兽，银色的毛发，有5条腿；有蛋蛋兽，紫色，8条腿。

    请根据上文，列出一个表格，包含物种名、颜色、腿数量。
    |物种名|颜色|腿数量|
    |亚古兽|金黄|2|
    |海星兽|粉色|5|
    |猫猫兽|橘色|4|
    |蜈蚣兽|漆黑|36|
    """
]

for text in texts:
    token_len = len(tokenizer._tokenize(text))
    print(text_generater(text, max_length=token_len + 15, top_k=1, use_cache=True, prefix='')[0]['generated_text'])
    print(text_generater(text, max_length=token_len + 15, do_sample=True, top_k=5)[0]['generated_text'])
```

![avatar](https://github.com/mymusise/CPM-TF2Transformer/raw/main/example-cpm.png)

You can try it on [colab](https://colab.research.google.com/github/mymusise/CPM-TF2Transformer/blob/main/demo-fp16.ipynb)

<a href="https://colab.research.google.com/github/mymusise/CPM-TF2Transformer/blob/main/demo-fp16.ipynb">
  <img alt="Build" src="https://colab.research.google.com/assets/colab-badge.svg">
</a>

