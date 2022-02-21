---
language:
- ru
tags:
- PyTorch
- Text2Image
thumbnail: "https://github.com/sberbank-ai/ru-clip"
---

# Model Card: ruCLIP
Disclaimer: The code for using model you can found [here](https://github.com/sberbank-ai/ru-clip).
# Model Details
The ruCLIP model was developed by researchers at SberDevices and Sber AI based on origin OpenAI paper.
# Model Type
The model uses a ViT-B/32 Transformer architecture (initialized from OpenAI checkpoint and freezed while training) as an image encoder and uses [ruGPT3Small](https://github.com/sberbank-ai/ru-gpts) as a text encoder. These encoders are trained to maximize the similarity of (image, text) pairs via a contrastive loss.
# Documents
Our habr [post](https://habr.com/ru/company/sberdevices/blog/564440/).
# Usage
Code for using model you can obtain in our [repo](https://github.com/sberbank-ai/ru-clip).

```
from clip.evaluate.utils import (
    get_text_batch, get_image_batch, get_tokenizer,
    show_test_images, load_weights_only
)
import torch

# Load model and tokenizer
model, args = load_weights_only("ViT-B/32-small")
model = model.cuda().float().eval()
tokenizer = get_tokenizer()
# Load test images and prepare for model
images, texts = show_test_images(args)
input_ids, attention_mask = get_text_batch(["Это " + desc for desc in texts], tokenizer, args)
img_input = get_image_batch(images, args.img_transform, args)
# Call model
with torch.no_grad():
    logits_per_image, logits_per_text = model(
        img_input={"x": img_input},
        text_input={"x": input_ids, "attention_mask": attention_mask}
    )
```

# Performance
We evaluate our model on CIFAR100 and CIFAR10 datasets.

zero-shot classification CIFAR100 top1 accuracy 0.4057; top5 accuracy 0.6975.

zero-shot classification CIFAR10 top1 accuracy 0.7803; top5 accuracy 0.9834.