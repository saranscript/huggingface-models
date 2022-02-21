---
tags:
- image-classification
- pytorch
datasets:
- imagenet
---

# Resnet50 Model from Torchvision

## Using the model

```
pip install modelz
```

```python
from modelz import ResnetModel

model = ResnetModel.from_pretrained('nateraw/resnet50')
ex_input = torch.rand(4, 3, 224, 224)
out = model(ex_input)
```