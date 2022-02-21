---
thumbnail: https://huggingface.co/front/thumbnails/dialogpt.png
language:
- en
tags:
- conversational
- transformers
datasets:
- GDC
metrics:
- perplexity
license: cc-by-4.0
widget:
- text: "Jag ska fika."
---

## DialoGPT_SV

This is a fine-tuned model of the DialoGPT (medium) on the Swedish Gothenburg Dialogue Corpus (GDC). It is intended to be used as a Swedish conversational system. The GDC dataset it's trained on is limited in scope, as it's from the transcription of dialogues of about 25 different social activities, including debates, academic seminars and situations. The dataset has about 108K turns. 

The perplexity achieved on the test and validation sets (from 80:10:10 split) are 27.81 and 27.81, respectivley. More information about the original pre-trained model can be found [here](https://huggingface.co/microsoft/DialoGPT-medium)

* Generation example from an interactive environment:

|Role | Response |
|---------|------------|
|User | Jag ska fika |
|Bot | ja det är ju så att jag kanske inte kan få den att göra det |
|User | tack så mycket |
|Bot | tack tack ses vi om sex vecko igen | 

Please, find the information about preprocessing, training and full details of the DialoGPT in the [original DialoGPT repository](https://github.com/microsoft/DialoGPT)

The paper for this work was accepted at the Northern Lights Deep Learning (NLDL) conference 2022. Arxiv paper: [https://arxiv.org/pdf/2110.06273.pdf](https://arxiv.org/pdf/2110.06273.pdf)

### How to use

Now we are ready to try out how the model works as a chatting partner!

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch
tokenizer = AutoTokenizer.from_pretrained("tosin/dialogpt_sv")
model = AutoModelForCausalLM.from_pretrained("tosin/dialogpt_sv")
# Let's chat for 5 lines
for step in range(5):
	# encode the new user input, add the eos_token and return a tensor in Pytorch
	new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')
	# append the new user input tokens to the chat history
	bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids
	# generated a response while limiting the total chat history to 1000 tokens, 
	chat_history_ids = model.generate(bot_input_ids, max_length=1000, pad_token_id=tokenizer.eos_token_id)
	# pretty print last ouput tokens from bot
	print("Swedish_GDC_Bot: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
