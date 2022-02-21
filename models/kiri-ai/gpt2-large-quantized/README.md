---
language: 
- en
---
# Pytorch int8 quantized version of gpt2-large

## Usage

Download the .bin file locally.
Load with:

Rest of the usage according to [original instructions](https://huggingface.co/gpt2-large).

```python
import torch

model = torch.load("path/to/pytorch_model_quantized.bin")
```
