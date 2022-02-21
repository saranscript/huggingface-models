---
language:
- ja
license: cc-by-sa-4.0
datasets:
- wikipedia
widget:
- text: "早稲田 大学 で 自然 言語 処理 を"
---

# nlp-waseda/gpt2-small-japanese-wikipedia

This model is Japanese GPT-2 pretrained on Japanese Wikipedia.

## Intended uses & limitations

You can use the raw model for text generation or fine-tune it to a downstream task.

Note that the texts should be segmented into words using Juman++ in advance.

### How to use

You can use this model directly with a pipeline for text generation. Since the generation relies on some randomness, we set a seed for reproducibility:

```python
>>> from transformers import pipeline, set_seed
>>> generator = pipeline('text-generation', model='nlp-waseda/gpt2-small-japanese-wikipedia')
>>> set_seed(42)
>>> generator("早稲田 大学 で 自然 言語 処理 を", max_length=30, do_sample=True, pad_token_id=2, num_return_sequences=5)
[{'generated_text': '早稲田 大学 で 自然 言語 処理 を 学び 、 1969 年 に は 同 大学院 を 修了 。  東京 芝浦 電気 株式 会社 に 就職 後 、 情報 処理'},
 {'generated_text': '早稲田 大学 で 自然 言語 処理 を 学び 、 帰国 後 は 立教 大学 理学部 助手 を 務めた 。 1978 年 に 神奈川 県立 湘南 高等 学校 校長 に 就任'},
 {'generated_text': '早稲田 大学 で 自然 言語 処理 を 研究 。 1972 年 に 早稲田 大学 文学部 ドイツ 文学 専攻 を 卒業 し 、 同 年 から 1979 年 まで 上智 大学'},
 {'generated_text': '早稲田 大学 で 自然 言語 処理 を 専攻 する 。 1979 年 東京 農工 大学 農学 部 卒業 。 1980 年 同 大学院 農学 研究 科 修士 課程 修了 。'},
 {'generated_text': '早稲田 大学 で 自然 言語 処理 を 専攻 し ながら 、 日本 で 活動 する 自然 言語 研究 家 。 大学 時代 は 東京 大学 理学部 の 助手 を 務め'}]
```

Here is how to use this model to get the features of a given text in PyTorch:

```python
from transformers import ReformerTokenizer, GPT2Model
tokenizer = ReformerTokenizer.from_pretrained('nlp-waseda/gpt2-small-japanese-wikipedia')
model = GPT2Model.from_pretrained('nlp-waseda/gpt2-small-japanese-wikipedia')
text = "早稲田 大学 で 自然 言語 処理 を"
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```

## Training data

The GPT-2 model was pretrained on Japanese Wikipedia, dumped on 2021-12-20.

## Training procedure

### Preprocessing

The texts are normalized using zenhan, segmented into words using Juman++, and tokenized using SentencePiece. Juman++ 2.0.0-rc3 was used for pretraining.

The model was trained on 8 NVIDIA A100 GPUs.
