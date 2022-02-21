# T5-base data to text model specialized for Finance NLG

 __simple version__
 
 This model was trained on a limited number of indicators, values and dates

----
## Usage (HuggingFace Transformers)



#### Call the model

```python

from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
  
tokenizer = AutoTokenizer.from_pretrained("yseop/FNP_T5_D2T_simple")

model = AutoModelForSeq2SeqLM.from_pretrained("yseop/FNP_T5_D2T_simple")


text = ["Group profit | valIs | $ 10 && € $10  | dTime | in 2019"]

```
#### Choose a generation method 

```python


input_ids = tokenizer.encode(": {}".format(text), return_tensors="pt")
p=0.72
k=40

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