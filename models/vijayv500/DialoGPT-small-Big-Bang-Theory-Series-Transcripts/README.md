---

tags:
- conversational
license: mit
---
## I fine-tuned DialoGPT-small model on "The Big Bang Theory" TV Series dataset from Kaggle (https://www.kaggle.com/mitramir5/the-big-bang-theory-series-transcript)




```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch
tokenizer = AutoTokenizer.from_pretrained("vijayv500/DialoGPT-small-Big-Bang-Theory-Series-Transcripts")
model = AutoModelForCausalLM.from_pretrained("vijayv500/DialoGPT-small-Big-Bang-Theory-Series-Transcripts")
# Let's chat for 5 lines
for step in range(5):
	# encode the new user input, add the eos_token and return a tensor in Pytorch
	new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')
	# append the new user input tokens to the chat history
	bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids
	# generated a response while limiting the total chat history to 1000 tokens, 
    chat_history_ids = model.generate(
        bot_input_ids, max_length=200,
        pad_token_id=tokenizer.eos_token_id,  
        no_repeat_ngram_size=3,       
        do_sample=True, 
        top_k=100, 
        top_p=0.7,
        temperature = 0.8
    )
    	# pretty print last ouput tokens from bot
    print("TBBT Bot: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
```