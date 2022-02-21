# T5-base data to text model specialized for Finance NLG

__complete version__

----
## Usage (HuggingFace Transformers)



#### Call the model

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
  
tokenizer = AutoTokenizer.from_pretrained("yseop/FNP_T5_D2T_complete")

model = AutoModelForSeq2SeqLM.from_pretrained("yseop/FNP_T5_D2T_complete")


text = ["Group profit | valIs | € 115.7 million && € 115.7 million | dTime | in 2019"]

```
#### Choose a generation method 

```python


input_ids = tokenizer.encode(": {}".format(text), return_tensors="pt")
p = 0.82
k = 90

outputs = model.generate(input_ids,
                         do_sample=True,
                        top_p=p,
                        top_k=k,
                        early_stopping=True)

print(tokenizer.decode(outputs[0]))

```



```python

input_ids = tokenizer.encode(": {}".format(text), return_tensors="pt")

outputs = model.generate(input_ids, 
                         max_length=200, 
                         num_beams=2, repetition_penalty=2.5, 
                         top_k=50, top_p=0.98,
                         length_penalty=1.0,
                         early_stopping=True)

print(tokenizer.decode(outputs[0]))


```



**Created by:** [Yseop](https://www.yseop.com/) | Pioneer in Natural Language Generation (NLG) technology. Scaling human expertise through Natural Language Generation.