### Model information
  * language : English
  * fine tuning data : [squad 2.0](https://rajpurkar.github.io/SQuAD-explorer/)
  * License : CC-BY-SA 4.0
  * Base model : [xlm-roberta-base](https://huggingface.co/xlm-roberta-base)
  * input : question, context
  * output : answer

----
### Train information
 * train_runtime : 7562.859 
 * train_steps_per_second : 1.077
 * training_loss : 0.9661213896603117
 * epoch: 3.0
 
----

### How to use
```
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained (
"seongju/squadv2-xlm-roberta-base"
)

model = AutoModelForSequenceClassification.from_pretrained (
"seongju/squadv2-xlm-roberta-base"
)
```