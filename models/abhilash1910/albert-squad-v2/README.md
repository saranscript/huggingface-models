## Albert Transformer on SQuAD-v2

Training is done on the [SQuAD_v2](https://rajpurkar.github.io/SQuAD-explorer/) dataset. The model can be accessed via HuggingFace:

## Model Specifications

We have used the following parameters:

- num_train_epochs=0.25,              
- per_device_train_batch_size=5,    
- per_device_eval_batch_size=10,  
- warmup_steps=100,                
- weight_decay=0.01,               

## Usage Specifications

```python
from transformers import AutoTokenizer,AutoModelForQuestionAnswering
from transformers import pipeline
model=AutoModelForQuestionAnswering.from_pretrained('abhilash1910/albert-squad-v2')
tokenizer=AutoTokenizer.from_pretrained('abhilash1910/albert-squad-v2')
nlp_QA=pipeline('question-answering',model=model,tokenizer=tokenizer)
QA_inp={
    'question': 'How many parameters does Bert large have?',
    'context': 'Bert large is really big... it has 24 layers, for a total of 340M parameters.Altogether it is 1.34 GB so expect it to take a couple minutes to download to your Colab instance.'
}
result=nlp_QA(QA_inp)
result
```
## Result

The result is:


{'answer': '340M', 'end': 65, 'score': 0.14847151935100555, 'start': 61}

---
language:
- en
license: apache-2.0
datasets:
- squad_v2

---
