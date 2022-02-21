---
language: zh
widget:
- text: "晓日千红"
- text: "长街躞蹀"
---


# gen-gpt2-medium-chinese


# Overview

- **Language model**: GPT2-Medium
- **Model size**: 68M 
- **Language**: Chinese

# Example

```python
from transformers import TFGPT2LMHeadModel,AutoTokenizer
from transformers import TextGenerationPipeline

mode_name = 'liam168/gen-gpt2-medium-chinese'
tokenizer = AutoTokenizer.from_pretrained(mode_name)
model = TFGPT2LMHeadModel.from_pretrained(mode_name)

text_generator = TextGenerationPipeline(model, tokenizer)

print(text_generator("晓日千红", max_length=64, do_sample=True))
print(text_generator("加餐小语", max_length=50, do_sample=False))
```
输出
```text
[{'generated_text': '晓日千红 独 远 客 。 孤 夜 云 云 梦 到 冷 。 著 剩 笑 、 人 远 。 灯 啼 鸦 最 回 吟 。 望 ， 枕 付 孤 灯 、 客 。 对 梅 残 照 偏 相 思 ， 玉 弦 语 。 翠 台 新 妆 、 沉 、 登 临 水 。 空'}]
[{'generated_text': '加餐小语 有 有 骨 ， 有 人 诗 成 自 远 诗 。 死 了 自 喜 乐 ， 独 撑 天 下 诗 事 小 诗 柴 。 桃 花 谁 知 何 处 何 处 高 吟 诗 从 今 死 火 ， 此 事'}]
```
