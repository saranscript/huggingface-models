---
tags:
- conversational
---

# Hank Hill ChatBot

This is an instance of microsoft/DialoGPT-small trained on a tv show character, Hank Hill from King of The Hill. The data comes from a csv file that contains character lines from the first 5 seasons of the show. Updated some portion of the data to accurately show Hank's famous pronunciation of the word "what" with "hwhat". Chat with the model:

## Issues

Occasionally the chatbot just responds with just multiple '!' characters. The chatbot frequently responds with "I'm not your buddy, pal" to uncomfortable/strange prompts/messages. Still working on a fix for those known issues.

```Python
from transformers import AutoTokenizer, AutoModelWithLMHead
  
tokenizer = AutoTokenizer.from_pretrained("tngo/DialoGPT-small-HankHill")

model = AutoModelWithLMHead.from_pretrained("tngo/DialoGPT-small-HankHill")

# Let's chat for 4 lines
for step in range(4):
    new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')

    bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids

    chat_history_ids = model.generate(
        bot_input_ids, max_length=200,
        pad_token_id=tokenizer.eos_token_id,  
        no_repeat_ngram_size=3,       
        do_sample=True, 
        top_k=100, 
        top_p=0.7,
        temperature=0.8
    )
    
    print("Hank Hill Bot: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
```