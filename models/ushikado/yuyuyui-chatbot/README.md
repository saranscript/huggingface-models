---
language: ja
inference: false
---

# yuyuyui-chatbot

This model is based on [rinna/japanese-gpt2-medium](https://huggingface.co/rinna/japanese-gpt2-medium) and finetuned on Yuyuyui scenario corpus.

## Usage

The model takes a sequence of utterances (context) to generate a subsequent utterance (response). Each utterance begins with a **character token** and ends with an **EOS token**. Use the unspecified character token `<某>` for user inputs.

Put a character token after your question or query to generate a response from a specific character. In this case, make sure that an EOS token is not appended automatically by the tokenizer. Otherwise the model will interpret the trailing EOS as an empty utterance and try to add another random character token.

Simple example:

```python
from transformers import T5Tokenizer, AutoModelForCausalLM

tokenizer = T5Tokenizer.from_pretrained("ushikado/yuyuyui-chatbot")
model = AutoModelForCausalLM.from_pretrained("ushikado/yuyuyui-chatbot")

query_text = "<某>神樹様について教えてください。</s><上里 ひなた>"
input_tensor = tokenizer.encode(query_text, add_special_tokens=False, return_tensors="pt")
output_list = model.generate(input_tensor, max_length=100, do_sample=True, pad_token_id=tokenizer.eos_token_id)
output_text = tokenizer.decode(output_list[0])
print(output_text)
"""
<某> 神樹様について教えてください。</s> <上里 ひなた> 造反神は、神樹様の分裂を煽り出して、神樹様の中の一体感を高める存在です。</s>
"""
```

Accumulate dialog history to make responses more context-aware:

```python
class Interlocutor():
    def __init__(self, tokenizer, model, character_token, max_context_length=512, max_response_length=128):
        self.tokenizer = tokenizer
        self.model = model
        self.character_token = character_token
        self.max_context_length = max_context_length
        self.max_response_length = max_response_length
        self.context = ""
        return
    
    def generate(self, query):
        nanigashi = self.tokenizer.additional_special_tokens[0]
        nanigashi_id = self.tokenizer.additional_special_tokens_ids[0]
        self.context += nanigashi + query + self.tokenizer.eos_token + self.character_token
        context_tensor = self.tokenizer.encode(self.context, add_special_tokens=False, return_tensors="pt")
        context_length = context_tensor.size()[-1]
        if self.max_context_length < context_length:
            context_tensor = context_tensor.narrow(1, context_length - self.max_context_length, self.max_context_length)
            context_length = context_tensor.size()[-1]
        max_length = context_length + self.max_response_length
        context_tensor = self.model.generate(context_tensor, do_sample=True, max_length=max_length,
                                             pad_token_id=self.tokenizer.eos_token_id)
        self.context = re.sub(self.tokenizer.eos_token, "", self.tokenizer.decode(context_tensor[0]))
        response = self.context[self.context.rindex(self.character_token) + len(self.character_token) : ].strip()
        print(response)

interlocutor = Interlocutor(tokenizer, model, "<加賀城 雀>")
interlocutor.generate("何しようかな。")
"""
そうだなぁ。せっかく徳島に来たんだから、何か食べたいよなー。</s>
"""
interlocutor.generate("例えば？")
"""
スパムとかいう高級料理はちょっとなぁ。あとは可愛い雑貨とか、おやつとか。</s>
"""
interlocutor.generate("徳島ラーメンじゃないの？")
"""
あー、確か徳島ラーメンってのがあって、それも美味しいんだよね。</s>
"""
interlocutor.generate("ここから近いお店があるんだって。行ってみよう！")
"""
わー! 何だか賑やかでいい感じだね。</s>
"""
interlocutor.generate("さっそく注文するね。")
"""
んー! ずっーと揚げ鶏が好きだったけど、今日は初めてまるまる鶏肉を注文してみるよ。</s>
"""
print(interlocutor.context)
"""
<某> 何しようかな。</s> <加賀城 雀> そうだなぁ。せっかく徳島に来たんだから、何か食べたいよなー。</s> <某> 例えば?</s> <加賀城 雀> スパムとかいう高級料理はちょっとなぁ。あとは可愛い雑貨とか、おやつとか。</s> <某> 徳島ラーメンじゃないの?</s> <加賀城 雀> あー、確か徳島ラーメンってのがあって、それも美味しいんだよね。</s> <某> ここから近いお店があるんだって。行ってみよう!</s> <加賀城 雀> わー! 何だか賑やかでいい感じだね。</s> <某> さっそく注文するね。</s> <加賀城 雀> んー! ずっーと揚げ鶏が好きだったけど、今日は初めてまるまる鶏肉を注文してみるよ。</s>
"""
```

## List of character tokens

`<某>` is _unspecified (nanigashi)_. Use for user inputs or mobs.

```plain
<某>
<結城 友奈>
<東郷 美森>
<犬吠埼 風>
<犬吠埼 樹>
<三好 夏凜>
<乃木 園子>
<鷲尾 須美>
<三ノ輪 銀>
<乃木 若葉>
<上里 ひなた>
<土居 球子>
<伊予島 杏>
<郡 千景>
<高嶋 友奈>
<白鳥 歌野>
<藤森 水都>
<秋原 雪花>
<古波蔵 棗>
<楠 芽吹>
<加賀城 雀>
<弥勒 夕海子>
<山伏 しずく>
<山伏 シズク>
<国土 亜耶>
<赤嶺 友奈>
<弥勒 蓮華>
<桐生 静>
<安芸 真鈴>
<花本 美佳>
```

## Licence

TBD.