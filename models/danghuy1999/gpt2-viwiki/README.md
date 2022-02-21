---
language: vi
tags:
  - gpt2-viwiki

license: mit
---

# GPT-2 Fine-tuning in Vietnamese Wikipedia

## Model description

This is a Vietnamese GPT-2 model which is finetuned on the [Latest pages articles of Vietnamese Wikipedia](https://dumps.wikimedia.org/viwiki/latest/viwiki-latest-pages-articles.xml.bz2).

## Dataset

The dataset is about 800MB, includes many articles from Wikipedia.

## How to use

You can use this model to:

- Tokenize Vietnamese sentences with GPT2Tokenizer.
- Generate text seems like a Wikipedia article.
- Finetune it to other downstream tasks.

Here is how to use the model to generate text in Pytorch:

```python
import torch
from transformers import GPT2Tokenizer, GPT2LMHeadModel

tokenizer = GPT2Tokenizer.from_pretrained('danghuy1999/gpt2-viwiki')
model = GPT2LMHeadModel.from_pretrained('danghuy1999/gpt2-viwiki').to('cuda')

text = "Albert Einstein là nhà vật lý học tạo ra thuyết lượng tử"
input_ids = tokenizer.encode(text, return_tensors='pt').to('cuda')
max_length = 100

sample_outputs = model.generate(input_ids,pad_token_id=tokenizer.eos_token_id,
                                   do_sample=True,
                                   max_length=max_length,
                                   min_length=max_length,
                                   top_k=40,
                                   num_beams=5,
                                   early_stopping=True,
                                   no_repeat_ngram_size=2,
                                   num_return_sequences=3)

for i, sample_output in enumerate(sample_outputs):
    print(">> Generated text {}\n\n{}".format(i+1, tokenizer.decode(sample_output.tolist())))
    print('\n---')
```

And the results are:

```bash
>> Generated text 1

Albert Einstein là nhà vật lý học tạo ra thuyết lượng tử.

Mặc dù thuyết tương đối tổng quát không được áp dụng rộng rãi trong nhiều lĩnh vực khác nhau, nhưng các nhà lý thuyết đã đưa ra khái niệm rộng hơn về tính chất của vật chất. Một trong những nghiên cứu của Albert Einstein về sự tồn tại của hệ quy chiếu quán tính, ông đã đề xuất rằng một lực hấp dẫn có thể có khối lượng bằng năng lượng của nó. Tuy nhiên, những người cho rằng

---
>> Generated text 2

Albert Einstein là nhà vật lý học tạo ra thuyết lượng tử. Tuy nhiên, thuyết tương đối hẹp không phải là lý thuyết của Einstein.

Cho đến tận cuối thế kỷ 19, Albert Einstein đã chứng minh được sự tồn tại của lực hấp dẫn trong một số trường hợp đặc biệt. Năm 1915, ông đưa ra khái niệm "khối lượng" để miêu tả chuyển động lượng của một hạt bằng khối lượng nghỉ của nó. Ông cho rằng năng lượng "m" là một thành phần của

---
>> Generated text 3

Albert Einstein là nhà vật lý học tạo ra thuyết lượng tử. Tuy nhiên, thuyết tương đối hẹp không được chấp nhận rộng rãi bởi các nhà lý thuyết.

Một trong những nghiên cứu của Einstein về tính chất của lực hấp dẫn là vào năm 1905, ông đã đưa ra một khái niệm về lực học. Ông đã phát biểu rằng nếu một hạt mang điện tích dương, nó có thể chuyển đổi năng lượng của nó thành các hạt khác. Năm 1915, Arthur Eddington phát minh ra

---
```

You can do the same with **Tensorflow** by using the model **TFGPT2Tokenizer** instead.
