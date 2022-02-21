---
- Text Generation
- PyTorch
- Transformers
- gpt_neo
- text generation
---

## Petrained Model Description: Open Source Version of GPT-3
Generative Pre-trained Transformer 3 (GPT-3) is an autoregressive language model that uses deep learning to produce human-like text.
It is the third-generation language prediction model in the GPT-n series (and the successor to GPT-2) created by OpenAI

GPT-Neo (125M) is a transformer model designed using EleutherAI's replication of the GPT-3 architecture. GPT-Neo refers to the class of models, while 125M represents the number of parameters of this particular pre-trained model.
and first released in this [repository](https://github.com/EleutherAI/gpt-neo). 


## Fine-tuned Model Description: GPT-3 fine-tuned Multi-XScience
The Open Source version of GPT-3: GPT-Neo(125M) has been fine-tuned on a dataset called "Multi-XScience": [Multi-XScience_Repository](https://github.com/yaolu/Multi-XScience): A Large-scale Dataset for Extreme Multi-document Summarization of Scientific Articles.    

I first fine-tuned and then deployed it using Google "Material Design" (on Anvil): [Abir Scientific text Generator](https://abir-scientific-text-generator.anvil.app/)  

By fine-tuning GPT-Neo(Open Source version of GPT-3), on Multi-XScience dataset, the model is now able to generate scientific texts(even better than GPT-J(6B).   
Try putting the prompt "attention is all" on both my [Abir Scientific text Generator](https://abir-scientific-text-generator.anvil.app/)  and on the [ GPT-J Eleuther.ai Demo](https://6b.eleuther.ai/) to understand what I mean.   
And Here's a demonstration video for this. [Video real-time Demontration](https://www.youtube.com/watch?v=XP8uZfnCYQI)