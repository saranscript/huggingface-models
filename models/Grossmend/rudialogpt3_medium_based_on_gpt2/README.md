---
language: 
- ru
thumbnail:
tags:
- convAI
- conversational
---

DialoGPT on Russian language

Article on Habr: https://habr.com/ru/company/icl_services/blog/548244/

Git: https://github.com/Grossmend/DialoGPT


#### How to use

```python
import torch
from transformers import AutoModelForCausalLM, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("Grossmend/rudialogpt3_medium_based_on_gpt2")
model = AutoModelForCausalLM.from_pretrained("Grossmend/rudialogpt3_medium_based_on_gpt2")


def get_length_param(text: str) -> str:
    tokens_count = len(tokenizer.encode(text))
    if tokens_count <= 15:
        len_param = '1'
    elif tokens_count <= 50:
        len_param = '2'
    elif tokens_count <= 256:
        len_param = '3'
    else:
        len_param = '-'
    return len_param


for step in range(5):
    
    input_user = input("===> User:")
    
    # encode the new user input, add parameters and return a tensor in Pytorch
    new_user_input_ids = tokenizer.encode(f"|0|{get_length_param(input_user)}|" + input_user + tokenizer.eos_token +  "|1|1|", return_tensors="pt")

    # append the new user input tokens to the chat history
    bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids
    
    # generated a response
    chat_history_ids = model.generate(
        bot_input_ids,
        num_return_sequences=1,
        max_length=512,
        no_repeat_ngram_size=3,
        do_sample=True,
        top_k=50,
        top_p=0.9,
        temperature = 0.6,
        mask_token_id=tokenizer.mask_token_id,
        eos_token_id=tokenizer.eos_token_id,
        unk_token_id=tokenizer.unk_token_id,
        pad_token_id=tokenizer.pad_token_id,
        device='cpu',
    )
    
    # pretty print last ouput tokens from bot
    print(f"===> RuDialoGPT: {tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)}")
    
```