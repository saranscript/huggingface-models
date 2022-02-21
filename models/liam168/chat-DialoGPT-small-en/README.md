---
language: en
widget: 
- text: "I got a surprise for you, Morty."
license: apache-2.0
---


# liam168/chat-DialoGPT-small-en

## Model description

用英文聊天数据训练的模型；

### How to use

Now we are ready to try out how the model works as a chatting partner!

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

mode_name = 'liam168/chat-DialoGPT-small-en'
tokenizer = AutoTokenizer.from_pretrained(mode_name)
model = AutoModelForCausalLM.from_pretrained(mode_name)

# Let's chat for 5 lines
for step in range(5):
	# encode the new user input, add the eos_token and return a tensor in Pytorch
	new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')

	# append the new user input tokens to the chat history
	bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids

	# generated a response while limiting the total chat history to 1000 tokens, 
	chat_history_ids = model.generate(bot_input_ids, max_length=1000, pad_token_id=tokenizer.eos_token_id)

	# pretty print last ouput tokens from bot
	print("Answer: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
```
