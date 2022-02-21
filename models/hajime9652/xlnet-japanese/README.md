---
language: 
- ja
thumbnail: 
tags:
- xlnet
- lm-head
- causal-lm
license: 
datasets:
metrics:
---

# XLNet-japanese

## Model description
This model require Mecab and senetencepiece with XLNetTokenizer.
See details https://qiita.com/mkt3/items/4d0ae36f3f212aee8002

## Intended uses & limitations

#### How to use

```python
import MeCab
import subprocess

from transformers import (
    pipeline,
    XLNetLMHeadModel,
    XLNetTokenizer
)

class XLNet():
    def __init__(self):
        cmd = 'echo `mecab-config --dicdir`"/mecab-ipadic-neologd"'
        path = (subprocess.Popen(cmd, stdout=subprocess.PIPE, 
            shell=True).communicate()[0]).decode('utf-8')
        self.m = MeCab.Tagger(f"-Owakati -d {path}")

        self.gen_model = XLNetLMHeadModel.from_pretrained("hajime9652/xlnet-japanese")
        self.gen_tokenizer = XLNetTokenizer.from_pretrained("hajime9652/xlnet-japanese")
         
    def generate(self, prompt="福岡のご飯は美味しい。コンパクトで暮らしやすい街。"):
        prompt = self.m.parse(prompt)
        inputs = self.gen_tokenizer.encode(prompt, add_special_tokens=False, return_tensors="pt")
        prompt_length = len(self.gen_tokenizer.decode(inputs[0], skip_special_tokens=True, clean_up_tokenization_spaces=True))
        outputs = self.gen_model.generate(inputs, max_length=200, do_sample=True, top_p=0.95, top_k=60)
        generated = prompt + self.gen_tokenizer.decode(outputs[0])[prompt_length:]
        return generated
```

#### Limitations and bias

## Training data


## Training procedure

## Eval results

### 
See this documents https://qiita.com/mkt3/items/4d0ae36f3f212aee8002
published by https://github.com/mkt3