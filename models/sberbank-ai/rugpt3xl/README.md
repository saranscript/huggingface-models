---
language:
- ru
tags:
- PyTorch
- Transformers
thumbnail: "https://github.com/sberbank-ai/ru-gpts"
---

# rugpt3xl
Model was trained with 512 sequence length using [Deepspeed](https://github.com/microsoft/DeepSpeed) and [Megatron](https://github.com/NVIDIA/Megatron-LM) code by [SberDevices](https://sberdevices.ru/) team, on 80B tokens dataset for 4 epochs. After that model was finetuned 1 epoch with sequence length 2048.  
*Note! Model has sparse attention blocks.*

Total training time was around 10 days on 256 GPUs.  
Final perplexity on test set is `12.05`.
Model parameters: 1.3B.
