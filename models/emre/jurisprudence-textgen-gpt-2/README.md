---
language: tr

license: mit
---

# jurisprudence-textgen-gpt-2

Pretrained model on Turkish language using a causal language modeling (CLM) objective. 

## Model description of Original GPT-2
GPT-2 is a transformers model pretrained on a very large corpus of English data in a self-supervised fashion. This means it was pretrained on the raw texts only, with no humans labelling them in any way (which is why it can use lots of publicly available data) with an automatic process to generate inputs and labels from those texts. More precisely, it was trained to guess the next word in sentences.

More precisely, inputs are sequences of continuous text of a certain length and the targets are the same sequence, shifted one token (word or piece of word) to the right. The model uses internally a mask-mechanism to make sure the predictions for the token i only uses the inputs from 1 to i but not the future tokens.

This way, the model learns an inner representation of the English language that can then be used to extract features useful for downstream tasks. The model is best at what it was pretrained for however, which is generating texts from a prompt.

## Model description of jurisprudence-textgen-gpt-2
Jurisprudence-textgen-gpt-2 is a transformers model for tensorflow pretrained with 18950 Turkish court Jurisprudence text data which has been obtained from [Bilirkisi GITHUB REPO TRAIN DATA] (https://github.com/Bilirkisi/Bilirkisi/tree/main/train) with 5 epochs. 
Model Training results are:

Epoch 1/5
4986/4986 - 2770s 552ms/step - loss: 4.0122 - output_1_loss: 4.0122 - output_1_accuracy: 0.4544 

Epoch 2/5
4986/4986 - 2753s 552ms/step - loss: 2.7074 - output_1_loss: 2.7074 - output_1_accuracy: 0.5843 

Epoch 3/5
4986/4986 - 2754s 552ms/step - loss: 2.3411 - output_1_loss: 2.3411 - output_1_accuracy: 0.6214 

Epoch 4/5
4986/4986 - 2754s 552ms/step - loss: 2.1241 - output_1_loss: 2.1241 - output_1_accuracy: 0.6431 

Epoch 5/5
4986/4986 - 2754s 552ms/step - loss: 1.9647 - output_1_loss: 1.9647 - output_1_accuracy: 0.6597 

## Intended uses & limitations
You can use the raw model for text generation or fine-tune it to a turkish law included downstream task. See the
[model hub](https://huggingface.co/models?filter=gpt2) to look for fine-tuned versions on a task that interests you.

### How to use
You can use this model directly with a pipeline for text generation.
Here is how to use this model to get the features of a given text in Tensorflow:
```python
>>> from transformers import GPT2Tokenizer , TFGPT2LMHeadModel
>>> tokenizer = GPT2Tokenizer.from_pretrained('emre/jurisprudence-textgen-gpt-2')
>>> model = TFGPT2LMHeadModel.from_pretrained('emre/jurisprudence-textgen-gpt-2')
>>> text = "Tarafların karşılıklı iddia ve savunmalarına," #Translation: "Mutual claims and defenses of the parties,"
>>> # encoding the input text
>>> input_ids = tokenizer.encode(text, return_tensors='tf')
>>> # getting out output

>>> beam_output = model.generate(
>>>   input_ids,
>>>   max_length = 250,    
>>>   num_beams = 5,
>>>   temperature = 0.7,
>>>   no_repeat_ngram_size=2,
>>>   num_return_sequences=5
>>> )
>>> for i in range(5):
>>>   print(tokenizer.decode(beam_output[i]))
[{'generated_text': "Tarafların karşılıklı iddia ve savunmalarına, dayandıkları belgelere, temyiz olunan kararda yazılı gerekçelere göre yerinde bulunmayan temyiz sebeplerinin reddiyle usul ve kanuna uygun mahkeme kararının İİK. 366. ve HUMK. 438. maddeleri uyarınca (ONANMASINA), 13.10 YTL onama harcı temyiz edenden alındığından başkaca harç alınmasına mahal olmadığına, 25.12.2007 gününde oybirliğiyle karar verildi."},
 {'generated_text': "Tarafların karşılıklı iddia ve savunmalarına, dayandıkları belgelere, temyiz olunan kararda yazılı gerekçelere göre yerinde bulunmayan temyiz itirazlarının reddiyle usul ve kanuna uygun mahkeme kararının İİK. 366. ve HUMK. 438. maddeleri uyarınca (ONANMASINA), 15,60 TL onama harcı temyiz edenden alındığından başkaca harç alınmasına mahal olmadığına, 30/12/2009 gününde oybirliğiyle karar verildi."},
 {'generated_text': "Tarafların karşılıklı iddia ve savunmalarına, dayandıkları belgelere, temyiz olunan kararda yazılı gerekçelere göre yerinde bulunmayan temyiz sebeplerinin reddiyle usul ve kanuna uygun mahkeme kararının İİK. 366. ve HUMK. 438. maddeleri uyarınca (ONANMASINA), 15,60 TL onama harcı temyiz edenden alındığından başkaca harç alınmasına mahal olmadığına, 30/12/2009 gününde oybirliğiyle karar verildi."},
 {'generated_text': "Tarafların karşılıklı iddia ve savunmalarına, dayandıkları belgelere, temyiz olunan kararda yazılı gerekçelere göre yerinde bulunmayan temyiz sebeplerinin reddiyle usul ve kanuna uygun mahkeme kararının İİK. 366. ve HUMK. 438. maddeleri uyarınca (ONANMASINA), 13.10 YTL onama harcı temyiz edenden alındığından başkaca harç alınmasına mahal olmadığına, 25/12/2007 gününde oybirliğiyle karar verildi."},
 {'generated_text': "Tarafların karşılıklı iddia ve savunmalarına, dayandıkları belgelere, temyiz olunan kararda yazılı gerekçelere göre yerinde bulunmayan temyiz sebeplerinin reddiyle usul ve kanuna uygun mahkeme kararının İİK. 366. ve HUMK. 438. maddeleri uyarınca (ONANMASINA), 13.10 YTL onama harcı temyiz edenden alındığından başkaca harç alınmasına mahal olmadığına, 27/12/2007 gününde oybirliğiyle karar verildi."}]

```
### BibTeX entry and citation info
soon will be defined..