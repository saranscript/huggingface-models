---
language: ko
mask_token: "[MASK]"
widget:
  - text: 산악 자전거 경기는 상대적으로 새로운 [MASK] 1990년대에 활성화 되었다.
---

## Data-annotation-nlp-10 (BoostCamp AI)
위키피디아(스포츠) dataset 구축을 진행하면서 얻은 문장을 통해 bert 사전학습을 진행


## How to use
```python
from transformers import AutoTokenizer, BertForMaskedLM

model = BertForMaskedLM.from_pretrained("emeraldgoose/bert-base-v1-sports")
tokenizer = AutoTokenizer.from_pretrained("emeraldgoose/bert-base-v1-sports")

text = "산악 자전거 경기는 상대적으로 새로운 [MASK] 1990년대에 활성화 되었다."
inputs = tokenizer.encode(text, return_tensors='pt')

model.eval()
outputs = model(inputs)['logits']
predict = outputs.argmax(-1)[0]
print(tokenizer.decode(predict))
```