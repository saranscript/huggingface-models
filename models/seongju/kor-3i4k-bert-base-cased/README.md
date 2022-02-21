### Model information
  * language : Korean
  * fine tuning data : [kor_3i4k](https://huggingface.co/datasets/kor_3i4k)
  * License : CC-BY-SA 4.0
  * Base model : [bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased)
  * input : sentence
  * output : intent

----
### Train information
 * train_runtime: 2376.638
 * train_steps_per_second: 2.175
 * train_loss: 0.356829648599977
 * epoch: 3.0
 
----
### How to use
```
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained (
"seongju/kor-3i4k-bert-base-cased"
)

model = AutoModelForSequenceClassification.from_pretrained (
"seongju/kor-3i4k-bert-base-cased"
)
inputs = tokenizer(
"너는 지금 무엇을 하고 있니?",
 padding=True, truncation=True, max_length=128, return_tensors="pt"
 )
outputs = model(**inputs)
probs = outputs[0].softmax(1)
output = probs.argmax().item()
```