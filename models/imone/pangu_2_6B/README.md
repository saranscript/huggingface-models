# Pangu-Alpha 2.6B

## Model Description

PanGu-α is proposed by a joint technical team headed by PCNL. It is the first large-scale Chinese pre-trained language model with 200 billion parameters trained on 2048 Ascend processors using an automatic hybrid parallel training strategy. The whole training process is done on the “Peng Cheng Cloud Brain II” computing platform with the domestic deep learning framework called MindSpore. The PengCheng·PanGu-α pre-training model can support rich applications, has strong few-shot learning capabilities, and has outstanding performance in text generation tasks such as knowledge question and answer, knowledge retrieval, knowledge reasoning, and reading comprehension.

This repository contains PyTorch implementation of PanGu model, with
2.6 billion parameters pretrained weights (FP32 precision), converted from original MindSpore checkpoint.

## Usage (Text Generation)

Currently PanGu model is not supported by transformers, 
so `trust_remote_code=True` is required to load model implementation in this repo.

```python
from transformers import TextGenerationPipeline, AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("imone/pangu_2_6B", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("imone/pangu_2_6B", trust_remote_code=True)

text_generator = TextGenerationPipeline(model, tokenizer)
# greedy search
print(text_generator("中国和美国和日本和法国和加拿大和澳大利亚的首都分别是哪里？", max_length=50))
```

Expected output:
```python
[{'generated_text': '中国和美国和日本和法国和加拿大和澳大利亚的首都分别是哪里？\n中国北京,美国华盛顿,日本东京,法国巴黎,加拿大多伦多,澳大利亚悉尼,新西兰奥克兰,澳大利亚墨尔本,新西兰奥克兰,'}]
```
