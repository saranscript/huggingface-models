---
tags:
- conversational
- tagalog
- filipino

language:
- tl 

inference: false

datasets:
- gabtan99/pex-conversations
---

# Tagalog DialoGPT
A DialoGPT-medium model fine-tuned on Tagalog conversational data scraped from the web. This model is an output of a research on RoBERTa-based data augmentation for low resource languages. This is the baseline model which did not use any synthetic data in training. 

#  Latest release: July 25, 2021
* The model is currently only able to respond based on the history of 3 previous utterances before being limited. This is a result of the scarce amount of Tagalog conversations in our dataset. 

# Dataset
[PEx Conversations Dataset](https://huggingface.co/datasets/gabtan99/pex-conversations)

# Usage
Here is an example of using beam search for model inference.
```
for step in range(2): 
    # encode the new user input, add the eos_token and return a tensor in Pytorch
    new_user_input_ids = tokenizer.encode(input(">> User:") + tokenizer.eos_token, return_tensors='pt')

    # append the new user input tokens to the chat history
    bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if step > 0 else new_user_input_ids

    # we limit the generation to 512 tokens, each utterance in training had a maximum of 128 tokens
    chat_history_ids = model.generate(
        bot_input_ids, max_length=512,
        pad_token_id=tokenizer.eos_token_id,
        num_beams=5, 
        no_repeat_ngram_size=3
    )
    
    # pretty print last ouput tokens from bot
    print("DialoGPT: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))
```

# Training Script
[Fine-tuning script adapted from Spanish DialoGPT](https://colab.research.google.com/github/ncoop57/i-am-a-nerd/blob/master/_notebooks/2020-05-12-chatbot-part-1.ipynb)

# Research by
* [tyadrianpaule](https://huggingface.co/tyadrianpaule)
* [schuylerng](https://huggingface.co/schuylerng)
* [dcl127](https://huggingface.co/dcl127)