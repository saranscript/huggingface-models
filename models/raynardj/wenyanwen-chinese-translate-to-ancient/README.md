---
language:
- zh
- zh
tags:
- translation
- 文言文
- ancient
license: apache-2.0
widget:
- text: "轻轻的我走了，正如我轻轻的来。我轻轻的招手，作别西天的云彩。"
  example_title: "再别康桥"
- text: "当恐惧逝去，我会打开心眼，看清它的轨迹。"
  example_title: "沙丘"
- text: "暴力是无能者的最后手段"
  example_title: "基地"

---

# From modern Chinese to Ancient Chinese
> This model translate modern Chinese to Classical Chinese, so I guess who's interested in the problemset can speak at least modern Chinese, so... let me continue the documentation in Chinese

* 从现代文到文言文的翻译器, 欢迎前往[github文言诗词项目页面:渊, 讨论&加⭐️ ](https://github.com/raynardj/yuan)

* 还有同款的[🤗文言文到现代文模型](https://huggingface.co/raynardj/wenyanwen-ancient-translate-to-modern)，原文输入可以**断句** 也可以是**未断句**的哦

* 训练语料是就是九十多万句句对， [数据集链接📚](https://github.com/BangBOOM/Classical-Chinese)。

## 推荐的inference 通道
**注意**， 你必须将```generate```函数的```eos_token_id```设置为102就可以翻译出完整的语句， 不然翻译完了会有残留的语句(因为做熵的时候用pad标签=-100导致)。

目前huggingface 页面上compute按钮会有这个问题， 推荐使用以下代码来得到翻译结果🎻 
```python
from transformers import (
  EncoderDecoderModel,
  AutoTokenizer
)
PRETRAINED = "raynardj/wenyanwen-chinese-translate-to-ancient"
tokenizer = AutoTokenizer.from_pretrained(PRETRAINED)
model = EncoderDecoderModel.from_pretrained(PRETRAINED)

def inference(text):
    tk_kwargs = dict(
      truncation=True,
      max_length=128,
      padding="max_length",
      return_tensors='pt')
   
    inputs = tokenizer([text,],**tk_kwargs)
    with torch.no_grad():
        return tokenizer.batch_decode(
            model.generate(
            inputs.input_ids,
            attention_mask=inputs.attention_mask,
            num_beams=3,
            bos_token_id=101,
            eos_token_id=tokenizer.sep_token_id,
            pad_token_id=tokenizer.pad_token_id,
        ), skip_special_tokens=True)
```

## 目前版本的案例
> 大家如果有好玩的调戏案例， 也欢迎反馈

```python
>>> inference('你连一百块都不肯给我')
['不 肯 与 我 百 钱 。']
```

```python
>>> inference("他不能做长远的谋划")
['不 能 为 远 谋 。']
```

```python
>>> inference("我们要干一番大事业")
['吾 属 当 举 大 事 。']
```

```python
>>> inference("这感觉，已经不对，我努力，在挽回")
['此 之 谓 也 ， 已 不 可 矣 ， 我 勉 之 ， 以 回 之 。']
```

```python
>>> inference("轻轻地我走了， 正如我轻轻地来， 我挥一挥衣袖，不带走一片云彩")
['轻 我 行 ， 如 我 轻 来 ， 挥 袂 不 携 一 片 云 。']
```

## 其他文言诗词的资源
* [项目源代码 🌟, 欢迎+star提pr](https://github.com/raynardj/yuan)
* [跨语种搜索 🔎](https://huggingface.co/raynardj/xlsearch-cross-lang-search-zh-vs-classicical-cn)
* [现代文翻译古汉语的模型 ⛰](https://huggingface.co/raynardj/wenyanwen-chinese-translate-to-ancient)
* [古汉语到现代文的翻译模型, 输入可以是未断句的句子 🚀](https://huggingface.co/raynardj/wenyanwen-ancient-translate-to-modern)
* [断句模型 🗡](https://huggingface.co/raynardj/classical-chinese-punctuation-guwen-biaodian)
* [意境关键词 和 藏头写诗🤖](https://huggingface.co/raynardj/keywords-cangtou-chinese-poetry)
