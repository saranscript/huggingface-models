---
license: apache-2.0
tags:
- semantic-segmentation
- vision
datasets:
- ade20k
---

# BEiT (large-sized model, fine-tuned on ADE20k) 

BEiT model pre-trained in a self-supervised fashion on ImageNet-21k (14 million images, 21,841 classes) at resolution 224x224, and fine-tuned on [ADE20k]() (an important benchmark for semantic segmentation of images) at resolution 640x640. It was introduced in the paper [BEIT: BERT Pre-Training of Image Transformers](https://arxiv.org/abs/2106.08254) by Hangbo Bao, Li Dong and Furu Wei and first released in [this repository](https://github.com/microsoft/unilm/tree/master/beit). 

Disclaimer: The team releasing BEiT did not write a model card for this model so this model card has been written by the Hugging Face team.

## Model description

The BEiT model is a Vision Transformer (ViT), which is a transformer encoder model (BERT-like). In contrast to the original ViT model, BEiT is pretrained on a large collection of images in a self-supervised fashion, namely ImageNet-21k, at a resolution of 224x224 pixels. The pre-training objective for the model is to predict visual tokens from the encoder of OpenAI's DALL-E's VQ-VAE, based on masked patches.
Next, the model was fine-tuned in a supervised fashion on ImageNet (also referred to as ILSVRC2012), a dataset comprising 1 million images and 1,000 classes, also at resolution 224x224.

Images are presented to the model as a sequence of fixed-size patches (resolution 16x16), which are linearly embedded. Contrary to the original ViT models, BEiT models do use relative position embeddings (similar to T5) instead of absolute position embeddings, and perform classification of images by mean-pooling the final hidden states of the patches, instead of placing a linear layer on top of the final hidden state of the [CLS] token.

By pre-training the model, it learns an inner representation of images that can then be used to extract features useful for downstream tasks: for semantic segmentation, one can just add one of the decode heads available in the [mmseg library](https://github.com/open-mmlab/mmsegmentation) for example, and fine-tune the model in a supervised fashion on annotated images. This is what the authors did: they fine-tuned BEiT with an UperHead segmentation decode head, allowing it to obtain SOTA results on important benchmarks such as ADE20k and CityScapes.

## Intended uses & limitations

You can use the raw model for semantic segmentation of images. See the [model hub](https://huggingface.co/models?search=microsoft/beit) to look for fine-tuned versions on a task that interests you.

### How to use

Here is how to use this model for semantic segmentation:

```python
from transformers import BeitFeatureExtractor, BeitForSemanticSegmentation
from datasets import load_dataset
from PIL import Image

# load ADE20k image
ds = load_dataset("hf-internal-testing/fixtures_ade20k", split="test")

feature_extractor = BeitFeatureExtractor.from_pretrained('microsoft/beit-large-finetuned-ade-640-640')
model = BeitForImageClassification.from_pretrained('microsoft/beit-large-finetuned-ade-640-640')

inputs = feature_extractor(images=image, return_tensors="pt")
outputs = model(**inputs)
# logits are of shape (batch_size, num_labels, height/4, width/4)
logits = outputs.logits
```

Currently, both the feature extractor and model support PyTorch.

## Training data

This BEiT model was pretrained on [ImageNet-21k](http://www.image-net.org/), a dataset consisting of 14 million images and 21k classes, and fine-tuned on [ADE20k](http://sceneparsing.csail.mit.edu/), a dataset consisting of thousands of annotated images and 150 classes. 

## Training procedure

### Preprocessing

The exact details of preprocessing of images during training/validation can be found [here](https://github.com/microsoft/unilm/blob/master/beit/datasets.py). 

Images are cropped and padded to the same resolution (640x640) and normalized across the RGB channels with the ImageNet mean and standard deviation.

### Pretraining

For all pre-training related hyperparameters, we refer to page 15 of the [original paper](https://arxiv.org/abs/2106.08254).

## Evaluation results

For evaluation results on several image classification benchmarks, we refer to tables 1 and 2 of the original paper. Note that for fine-tuning, the best results are obtained with a higher resolution (384x384). Of course, increasing the model size will result in better performance.

### BibTeX entry and citation info

```@article{DBLP:journals/corr/abs-2106-08254,
  author    = {Hangbo Bao and
               Li Dong and
               Furu Wei},
  title     = {BEiT: {BERT} Pre-Training of Image Transformers},
  journal   = {CoRR},
  volume    = {abs/2106.08254},
  year      = {2021},
  url       = {https://arxiv.org/abs/2106.08254},
  archivePrefix = {arXiv},
  eprint    = {2106.08254},
  timestamp = {Tue, 29 Jun 2021 16:55:04 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2106-08254.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```