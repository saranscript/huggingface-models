---
thumbnail: https://huggingface.co/front/thumbnails/dialogpt.png
language:
- en
license: cc-by-4.0
tags:
- conversational
- transformers
datasets:
- multi_woz_v22
metrics:
- perplexity
widget:
- text: "I would like to have breakfast."
---

## DialoGPT_MWOZ

This is a fine-tuned model of DialoGPT (medium) on the MultiWOZ v2.2 dataset. It is intended to be used as a conversational system.
The dataset it's trained on is limited in scope, as it covers only certain domains such as restaurants, hotel, taxi, train, hospital and police.

The perplexity achieved on the test and validation sets are 10.25 and 10.71, respectively. More information about the original pre-trained model can be found [here](https://huggingface.co/microsoft/DialoGPT-medium)

* Generation example from an interactive environment:

|Role | Response |
|---------|------------|
|User | I would like to have breakfast. |
|Bot | There are several options for Chinese in the city centre. Are you looking for a particular price range? |
|User | I'm looking for free food |
|Bot | There are 4 Chinese restaurants that are in the cheap price range. 3 in centre and one in north. |
|User | Not good enough |
|Bot | How about Charlie Chan? It is a Chinese restaurant in the centre of town. |

Please find the information about preprocessing, training and full details of the DialoGPT in the [original DialoGPT repository](https://github.com/microsoft/DialoGPT)

The paper for this work was accepted at the Northern Lights Deep Learning (NLDL) conference 2022. Arxiv paper: [https://arxiv.org/pdf/2110.06273.pdf](https://arxiv.org/pdf/2110.06273.pdf)

### How to use

Now we are ready to try out how the model works as a chatting partner!

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch
tokenizer = AutoTokenizer.from_pretrained("tosin/dialogpt_mwoz")
model = AutoModelForCausalLM.from_pretrained("tosin/dialogpt_mwoz")
# Let's chat for 5 lines
for step in range(5):
	# encode the new user input, add the eos_token and return a tensor in Pytorch
	new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')
	# append the new user input tokens to the chat history
	bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids
	# generated a response while limiting the total chat history to 1000 tokens, 
	chat_history_ids = model.generate(bot_input_ids, max_length=1000, pad_token_id=tokenizer.eos_token_id)
	# pretty print last ouput tokens from bot
	print("DialoGPT_MWOZ_Bot: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
