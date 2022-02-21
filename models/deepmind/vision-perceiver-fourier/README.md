---
license: apache-2.0
tags:
datasets:
- imagenet
---

# Perceiver IO for vision (fixed Fourier position embeddings)

Perceiver IO model pre-trained on ImageNet (14 million images, 1,000 classes) at resolution 224x224. It was introduced in the paper [Perceiver IO: A General Architecture for Structured Inputs & Outputs](https://arxiv.org/abs/2107.14795) by Jaegle et al. and first released in [this repository](https://github.com/deepmind/deepmind-research/tree/master/perceiver). 

Disclaimer: The team releasing Perceiver IO did not write a model card for this model so this model card has been written by the Hugging Face team.

## Model description

Perceiver IO is a transformer encoder model that can be applied on any modality (text, images, audio, video, ...). The core idea is to employ the self-attention mechanism on a not-too-large set of latent vectors (e.g. 256 or 512), and only use the inputs to perform cross-attention with the latents. This allows for the time and memory requirements of the self-attention mechanism to not depend on the size of the inputs. 

To decode, the authors employ so-called decoder queries, which allow to flexibly decode the final hidden states of the latents to produce outputs of arbitrary size and semantics. For image classification, the output is a tensor containing the logits, of shape (batch_size, num_labels).

<img src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/perceiver_architecture.jpg" alt="drawing" width="600"/>

<small> Perceiver IO architecture.</small>

As the time and memory requirements of the self-attention mechanism don't depend on the size of the inputs, the Perceiver IO authors can train the model directly on raw pixel values, rather than on patches as is done in ViT. This particular model only adds fixed Fourier 2D position embeddings to the pixel values.

By pre-training the model, it learns an inner representation of images that can then be used to extract features useful for downstream tasks: if you have a dataset of labeled images for instance, you can train a standard classifier by replacing the classification decoder.

## Intended uses & limitations

You can use the raw model for image classification. See the [model hub](https://huggingface.co/models?search=deepmind/perceiver) to look for other fine-tuned versions on a task that may interest you.

### How to use

Here is how to use this model in PyTorch:

```python
from transformers import PerceiverFeatureExtractor, PerceiverForImageClassificationFourier
import requests
from PIL import Image

feature_extractor = PerceiverFeatureExtractor.from_pretrained("deepmind/vision-perceiver-fourier")
model = PerceiverForImageClassificationFourier.from_pretrained("deepmind/vision-perceiver-fourier")

url = "http://images.cocodataset.org/val2017/000000039769.jpg"
image = Image.open(requests.get(url, stream=True).raw)

# prepare input
inputs = feature_extractor(image, return_tensors="pt").pixel_values
# forward pass
outputs = model(inputs)
logits = outputs.logits
print("Predicted class:", model.config.id2label[logits.argmax(-1).item()])
>>> should print Predicted class: tabby, tabby cat
```

## Training data

This model was pretrained on [ImageNet](http://www.image-net.org/), a dataset consisting of 14 million images and 1k classes. 

## Training procedure

### Preprocessing

Images are center cropped and resized to a resolution of 224x224 and normalized across the RGB channels. Note that data augmentation was used during pre-training, as explained in Appendix H of the [paper](https://arxiv.org/abs/2107.14795).

### Pretraining

Hyperparameter details can be found in Appendix H of the [paper](https://arxiv.org/abs/2107.14795).

## Evaluation results

This model is able to achieve a top-1 accuracy of 79.0 on ImageNet-1k, and 84.5 when pre-trained on a large-scale dataset (JFT-300M, an internal dataset of Google).

### BibTeX entry and citation info

```bibtex
@article{DBLP:journals/corr/abs-2107-14795,
  author    = {Andrew Jaegle and
               Sebastian Borgeaud and
               Jean{-}Baptiste Alayrac and
               Carl Doersch and
               Catalin Ionescu and
               David Ding and
               Skanda Koppula and
               Daniel Zoran and
               Andrew Brock and
               Evan Shelhamer and
               Olivier J. H{\'{e}}naff and
               Matthew M. Botvinick and
               Andrew Zisserman and
               Oriol Vinyals and
               Jo{\~{a}}o Carreira},
  title     = {Perceiver {IO:} {A} General Architecture for Structured Inputs {\&}
               Outputs},
  journal   = {CoRR},
  volume    = {abs/2107.14795},
  year      = {2021},
  url       = {https://arxiv.org/abs/2107.14795},
  eprinttype = {arXiv},
  eprint    = {2107.14795},
  timestamp = {Tue, 03 Aug 2021 14:53:34 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2107-14795.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```