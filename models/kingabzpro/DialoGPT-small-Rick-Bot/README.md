---
language: English
datasets:
- Andrada Olteanu Rickmorty-Scripts
tags:
- conversational
- Transformers
- gpt2
- Chatbot
- Rick&Morty
license: apache-2.0
metrics:
- Perplexity 
---
# Source Code
[<img src="https://api.flatworld.co/wp-content/uploads/2020/10/DAGsHub-Logo.png" alt="dagshub" width="150"/>](https://dagshub.com/kingabzpro/DailoGPT-RickBot)

[![DAGsHub](https://img.shields.io/badge/github-DailoGPT_RickBot-ffbf00?logo=github&color=black&style=for-the-badge)](https://github.com/kingabzpro/DailoGPT-RickBot)
# Testing

```python
tokenizer = AutoTokenizer.from_pretrained('kingabzpro/DialoGPT-small-Rick-Bot')
model = AutoModelWithLMHead.from_pretrained('kingabzpro/DialoGPT-small-Rick-Bot')
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
        no_repeat_ngram_size=3,       
        do_sample=True, 
        top_k=100, 
        top_p=0.7,
        temperature=0.8
    )
    
    # pretty print last ouput tokens from bot
    print("RickBot: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
```

**Result**

 perplexity : 8.53