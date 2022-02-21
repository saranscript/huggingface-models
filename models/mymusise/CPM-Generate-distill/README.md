---
language: zh
widget:
- text: "天下熙熙，"
- text: "天气不错，"
---

<h1 align="center">
CPM-Generate-distill
</h1>

CPM(Chinese Pre-Trained Language Models), which has 2.6B parameters, made by the research team of Beijing Zhiyuan Institute of artificial intelligence and Tsinghua University @TsinghuaAI.

[repo: CPM-Generate](https://github.com/TsinghuaAI/CPM-Generate)
The One Thing You Need to Know is this model is not uploaded by official, the conver script is [here](https://github.com/mymusise/CPM-TF2Transformer/blob/main/transfor_CMP.ipynb)

And the `CPM-Generate-distill` is the distill model of `CPM`.


# How to use

How to use this model directly from the 🤗/transformers library:

```python
from transformers import XLNetTokenizer, TFGPT2LMHeadModel
from transformers import TextGenerationPipeline
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

tokenizer = XLNetTokenizer.from_pretrained('mymusise/CPM-Generate-distill')
model = TFGPT2LMHeadModel.from_pretrained("mymusise/CPM-Generate-distill")

text_generater = TextGenerationPipeline(model, tokenizer)

print(text_generater("天下熙熙，", max_length=15, top_k=1, use_cache=True, prefix=''))
```

![avatar](https://github.com/mymusise/CPM-TF2Transformer/raw/main/example-cpm-distill.jpeg)
