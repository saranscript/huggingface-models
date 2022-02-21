---
thumbnail: https://cdn.discordapp.com/app-icons/870239976690970625/c02cae78ae105f07969cfd8f8ea3d0a0.png
tags:
- conversational
license: mit
---
# THIS AI IS OUTDATED. See [Aeona](https://huggingface.co/deepparag/Aeona)
An generative AI made using [microsoft/DialoGPT-small](https://huggingface.co/microsoft/DialoGPT-small).

Trained on:

     https://www.kaggle.com/Cornell-University/movie-dialog-corpus

     https://www.kaggle.com/jef1056/discord-data


     
[Live Demo](https://dumbot-331213.uc.r.appspot.com/)
 
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