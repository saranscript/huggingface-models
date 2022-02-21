# GPT-Neo for Conversation - Test 2.7B Model - 3 Epoch

- trained for **three epochs** with deepspeed
- used the Wizard of Wikipedia dataset parsed into a chat transcript structure as input  data 
- model is too big for inference API, but you can test it in a Colab notebook [here](https://colab.research.google.com/gist/pszemraj/bd9792333bb41933ee747fd005023b67/gpt-neo-for-conversation-test-2-7b-model-3-epoch.ipynb), which will also explain a bit more of the chatbot-like structure.
  - for more details / ideas on how to deploy a chatbot like this, check out the github repo [here](https://github.com/pszemraj/ai-msgbot).