---
thumbnail: https://images-ext-2.discordapp.net/external/IaDAOIgiVKpnDGgsqAsVEW5jgwIHprFc3dSmlW3U0Ro/%3Fsize%3D4096/https/cdn.discordapp.com/avatars/931226824753700934/51db9904887a38dca03238f9b3479594.png
tags:
- conversational
license: mit
---
An generative AI made using [microsoft/DialoGPT-small](https://huggingface.co/microsoft/DialoGPT-small).

# AEONA
 Note the AI is still learning so expect very frequent updates!
 Soon a sample AIML project and a API will be released! 
# Free API with the AIML backend!
[API](https://rapidapi.com/76multi@gmail.com/api/aeona2/)
[Website using the API](https://Aeona.repl.co/chat)

Context is broken right now.
So only the first message works
## Goals
 The goal is to create an AI which will work with AIML in order to create the most human like AI.
 
 #### Why not an AI on its own?
 For AI it is not possible (realistically) to learn about the user and store data on them, when compared to an AIML which can even execute code!
 The goal of the AI is to generate responses where the AIML fails.
 
 Hence the goals becomes to make an AI which has a wide variety of knowledge, yet be as small as possible!
 So we use 3 dataset:-
 1. [Movielines](https://www.kaggle.com/Cornell-University/movie-dialog-corpus) The movie lines promote longer and more thought out responses but it can be very random. About 200k lines!
 2. [Discord Messages](https://www.kaggle.com/jef1056/discord-data) The messages are on a wide variety of topics filtered and removed spam which makes the AI highly random but gives it a very random response to every days questions! about 120 million messages!
 3. Custom dataset scrapped from my messages, These messages are very narrow teaching this dataset and sending a random reply will make the AI say sorry loads of time!
    
## Training
  The Discord Messages Dataset simply dwarfs the other datasets, Hence the data sets are repeated.
  This leads to them covering each others issues!
## Usage
Example:
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
  
tokenizer = AutoTokenizer.from_pretrained("deepparag/DumBot")
model = AutoModelWithLMHead.from_pretrained("deepparag/DumBot")
# Let's chat for 4 lines
for step in range(4):
    # encode the new user input, add the eos_token and return a tensor in Pytorch
    new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')
    # print(new_user_input_ids)
    # append the new user input tokens to the chat history
    bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids
    # generated a response while limiting the total chat history to 1000 tokens, 
    chat_history_ids = model.generate(
        bot_input_ids, max_length=200,
        pad_token_id=tokenizer.eos_token_id,  
        no_repeat_ngram_size=4,       
        do_sample=True, 
        top_k=100, 
        top_p=0.7,
        temperature=0.8
    )
    
    # pretty print last ouput tokens from bot
    print("DumBot: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
```