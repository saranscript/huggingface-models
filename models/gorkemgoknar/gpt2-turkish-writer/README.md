---
language:
- tr
thumbnail:
tags:
- gpt2
- turkish
- aiwriter
- finetuned

license: apache-2.0
datasets:
- wikipedia-turkish
- custom-book-corpus
metrics:
- perplexity
- accuracy

widget:
- text: Bir zaman topu olan ama köpeği olmayan bir çocuk vardı. Parkta
  context: ''
- text: 'Uzun uzun sahile doğru baktı. Düşündüklerinden '
  context: ''
- text: Çok uzun zaman önce galaksinin uzak bir köşesinde...
  context: ''
- text: "'Bugün kendimi çok hasta hissediyorum' dedi. Karşısında "
  context: ''
---

# Turkish AI Writer based on GPT2-Small
# Türkçe Yapay Zeka Yazarı

## Model description

This model is enhanced version of gpt2-small-turkish finetuned version. In addition to 28-10-2020 Wikipedia Turkish article dump this model is trained with more than 400 classic novels and plays in Turkish (Including Dostoyevski, Shaekspeare, Dumas)

Base work has been done on Pierre Guillou tutorial as on this page.
(https://github.com/piegu/fastai-projects/blob/master/finetuning-English-GPT2-any-language-Portuguese-HuggingFace-fastaiv2.ipynb) 

Note that Since Turkish language is not close to English as in Porteguese instead  of training last 2 layers, last 3 layers are trained.

Code is converted to work with Fastai 2.X .
Using Google Colab for training. 

Current accuracy 36.3 %  , Perplexity : 44.75

Demo (using CPU inference) is available on: http://www.metayazar.com 

Models are available:

* [gpt2-small-tuned-tr] (https://huggingface.co/gorkemgoknar/gpt2-small-turkish)
* [gpt2-small-turkish-writer] (https://huggingface.co/gorkemgoknar/gpt2-turkish-writer)


## Intended uses & limitations

#### How to use

#### Install

```python
from transformers import AutoTokenizer, AutoModelWithLMHead
import torch

tokenizer = AutoTokenizer.from_pretrained("gorkemgoknar/gpt2-turkish-writer")
model = AutoModelWithLMHead.from_pretrained("gorkemgoknar/gpt2-turkish-writer")

# Get sequence length max of 1024
tokenizer.model_max_length=1024 

model.eval()  # disable dropout (or leave in train mode to finetune)

```

#### Generate 1 word
```python
# input sequence
text = "Bu yazıyı bilgisayar yazdı."
inputs = tokenizer(text, return_tensors="pt") 

# model output
outputs = model(**inputs, labels=inputs["input_ids"])
loss, logits = outputs[:2]
predicted_index = torch.argmax(logits[0, -1, :]).item()
predicted_text = tokenizer.decode([predicted_index])

# results
print('input text:', text)
print('predicted text:', predicted_text)

# input text: 
# predicted text:  

```

#### Generate Full Sequence
```python
# input sequence
text = "Bu yazıyı bilgisayar yazdı."
inputs = tokenizer(text, return_tensors="pt")

# model output using Top-k sampling text generation method
sample_outputs = model.generate(inputs.input_ids,
                                pad_token_id=50256,
                                do_sample=True, 
                                max_length=50, # put the token number you want
                                top_k=40,
                                num_return_sequences=1)

# generated sequence
for i, sample_output in enumerate(sample_outputs):
    print(">> Generated text {}\n\n{}".format(i+1, tokenizer.decode(sample_output.tolist())))

# >> Generated text
#    

```

#### Limitations and bias

The training data used for this model come from Turkish Wikipedia and books. We know it contains a lot of unfiltered content from the internet, which is far from neutral. Also not much pre-processing was done on books hence chapter names and page numbers can be seen on some cases. This is a work in progress.


## Training data

Wikipedia Turkish article dump as of 28-10-2020
Turkish book dataset of >400 classic novels

## Training procedure


## Eval results

| epoch	|train_loss	|valid_loss	|accuracy	|perplexity	|time   |
| ----- | --------      |---------      | ----------    | ---------     | ----- |
|0	|4.497828	|4.549605	|0.277328	|94.595070	|2:09:58|
|1	|4.503929	|4.519456	|0.275071	|91.785645	|2:04:30|
|2	|3.612716	|3.921146	|0.344802	|50.458256	|2:03:22|
|3	|3.777645	|4.072006	|0.326130	|58.674530	|1:56:14|
|4	|2.934462	|3.801303	|0.363719	|44.759476	|1:58:55|

Note: 1cycle rule training is used and epochs are at different times 
```

