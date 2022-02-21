### Model information
  * language : Korean
  * fine tuning data : [klue-tc (a.k.a. YNAT) ](https://klue-benchmark.com/tasks/66/overview/description)
  * License : CC-BY-SA 4.0
  * Base model : [bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased)
  * input : news headline
  * output : topic

----
### Train information
 * train_runtime: 1477.3876 
 * train_steps_per_second: 2.416 
 * train_loss: 0.3722160959110207 
 * epoch: 5.0
 
----
### How to use
```
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained (
"seongju/klue-tc-bert-base-multilingual-cased"
)

model = AutoModelForSequenceClassification.from_pretrained (
"seongju/klue-tc-bert-base-multilingual-cased"
)
mapping = {0: 'IT과학', 1: '경제', 2: '사회', 
3: '생활문화', 4: '세계', 5: '스포츠', 6: '정치'}
inputs = tokenizer(
"백신 회피 가능성? 남미에서 새로운 변이 바이러스 급속 확산 ",
 padding=True, truncation=True, max_length=128, return_tensors="pt"
 )
outputs = model(**inputs)
probs = outputs[0].softmax(1)
output = mapping[probs.argmax().item()]
```