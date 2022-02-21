---
tags:
- conversational
license: mit
---

## Finetuned DialoGPT model on Spanish Conversations

This model was finetuned from the original [DialoGPT-medium](https://huggingface.co/microsoft/DialoGPT-medium) model on subtitles from Spanish movies and telenovelas from the awesome [OpenSubtitle dataset](https://github.com/PolyAI-LDN/conversational-datasets/tree/master/opensubtitles).

DialoGPT paper: [https://arxiv.org/abs/1911.00536](https://arxiv.org/abs/1911.00536)

Some example dialog from the model:

|Role | Response |
|---------|--------|
|User | ¿Cómo está el clima hoy? |
| Bot | Muy bien. |
|User | Eso es bueno escuchar. ¿Vas a ir a la playa? |
| Bot | No, también puedo regresar. |
|User | Oh bien, bueno, iré a la playa más tarde. |
| Bot | ¡No! |
|User | ¿Qué está mal con eso? |
| Bot | ¡Cómo que no! |
|User | Estoy confundido, ¿por qué no puedo ir a la playa? |
| Bot | ¡Cómo que no! |
|User | Explícamelo por favor. |
| Bot | ¡No! |

## Using the model

Example code for trying out the model (taken directly from the [DialoGPT-medium](https://huggingface.co/microsoft/DialoGPT-medium) model card): 
```python
from transformers import AutoModelWithLMHead, AutoTokenizer
import torch


tokenizer = AutoTokenizer.from_pretrained("ncoop57/DiGPTame-medium")
model = AutoModelWithLMHead.from_pretrained("ncoop57/DiGPTame-medium")

# Let's chat for 5 lines
for step in range(5):
	# encode the new user input, add the eos_token and return a tensor in Pytorch
	new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')

	# append the new user input tokens to the chat history
	bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids

	# generated a response while limiting the total chat history to 1000 tokens, 
	chat_history_ids = model.generate(bot_input_ids, max_length=1000, pad_token_id=tokenizer.eos_token_id)

	# pretty print last ouput tokens from bot
	print("DialoGPT: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
```

## Training your own model

If you would like to finetune your own model or finetune this Spanish model, please checkout my blog post on that exact topic!
https://nathancooper.io/i-am-a-nerd/chatbot/deep-learning/gpt2/2020/05/12/chatbot-part-1.html