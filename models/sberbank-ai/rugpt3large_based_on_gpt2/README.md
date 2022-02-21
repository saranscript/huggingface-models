---
language:
- ru
tags:
- PyTorch
- Transformers
thumbnail: "https://github.com/sberbank-ai/ru-gpts"
---

# rugpt3large\_based\_on\_gpt2
Model was trained with sequence length 1024 using transformers lib by [SberDevices](https://sberdevices.ru/) team on 80B tokens for 3 epochs. After that model was finetuned 1 epoch with sequence length 2048. 

Total training time was around 14 days on 128 GPUs for 1024 context and few days on 16 GPUs for 2048 context.  
Final perplexity on test set is `13.6`.