This model was pretrained on the bookcorpus dataset using knowledge distillation.

The particularity of this model is that even though it shares the same architecture as BERT, it has a hidden size of 384 (half the hidden size of BERT) and 6 attention heads (hence the same head size of BERT).

The knowledge distillation was performed using multiple loss functions.

The weights of the model were initialized from scratch.

PS : the tokenizer is the same as the one of the model bert-base-uncased.



To load the model \& tokenizer :

````python
from transformers import AutoModelForMaskedLM, BertTokenizer

model_name = "eli4s/Bert-L12-h384-A6"
model = AutoModelForMaskedLM.from_pretrained(model_name)
tokenizer = BertTokenizer.from_pretrained(model_name)
````

To use it on a sentence :

````python
import torch

sentence = "Let's have a [MASK]."

model.eval()
inputs = tokenizer([sentence], padding='longest', return_tensors='pt')
output = model(inputs['input_ids'], attention_mask=inputs['attention_mask'])

mask_index = inputs['input_ids'].tolist()[0].index(103)
masked_token = output['logits'][0][mask_index].argmax(axis=-1)
predicted_token = tokenizer.decode(masked_token)

print(predicted_token)
````

Or we can also predict the n most relevant predictions :

````python
top_n = 5

vocab_size = model.config.vocab_size
logits = output['logits'][0][mask_index].tolist()
top_tokens = sorted(list(range(vocab_size)), key=lambda  i:logits[i], reverse=True)[:top_n]

tokenizer.decode(top_tokens)
````
