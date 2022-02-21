---
language:
- ru
tags:
- PyTorch
- Transformers
thumbnail: "https://github.com/sberbank-ai/ru-gpts"
---

# rugpt3medium\_based\_on\_gpt2

Model was trained with sequence length 1024 using transformers lib by [SberDevices](https://sberdevices.ru/) team on 80B tokens for 3 epoch. After that model was finetuned on 2048 context.

Total training time was around 16 days on 64 GPUs.  
Final perplexity on test set is `17.4`.
