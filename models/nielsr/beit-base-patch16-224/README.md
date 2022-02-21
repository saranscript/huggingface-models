---
license: apache-2.0
tags:
- image-classification
datasets:
- imagenet
- imagenet-21k
---

# BEiT (base-sized model, fine-tuned on ImageNet-1k after being intermediately fine-tuned on ImageNet-22k) 

BEiT (BERT pre-training of Image Transformers) model pre-trained in a self-supervised way on ImageNet-22k (14 million images, 21,841 classes) at resolution 224x224, and also fine-tuned on the same dataset at the same resolution. It was introduced in the paper [BEiT: BERT Pre-Training of Image Transformers](https://arxiv.org/abs/2106.08254) by Hangbo Bao, Li Dong and Furu Wei and first released in [this repository](https://github.com/microsoft/unilm/tree/master/beit). 

Disclaimer: The team releasing BEiT did not write a model card for this model so this model card has been written by the Hugging Face team.