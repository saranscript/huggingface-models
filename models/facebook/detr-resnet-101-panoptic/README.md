---
license: apache-2.0
tags:
- image-segmentation
datasets:
- coco
widget:
- src: https://huggingface.co/datasets/mishig/sample_images/resolve/main/dog-cat.jpg
  example_title: Dog & Cat
- src: https://huggingface.co/datasets/mishig/sample_images/resolve/main/construction-site.jpg
  example_title: Construction Site
- src: https://huggingface.co/datasets/mishig/sample_images/resolve/main/apple-orange.jpg
  example_title: Apple & Orange
---

# DETR (End-to-End Object Detection) model with ResNet-101 backbone

DEtection TRansformer (DETR) model trained end-to-end on COCO 2017 panoptic (118k annotated images). It was introduced in the paper [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872) by Carion et al. and first released in [this repository](https://github.com/facebookresearch/detr). 

Disclaimer: The team releasing DETR did not write a model card for this model so this model card has been written by the Hugging Face team.

## Model description

The DETR model is an encoder-decoder transformer with a convolutional backbone. Two heads are added on top of the decoder outputs in order to perform object detection: a linear layer for the class labels and a MLP (multi-layer perceptron) for the bounding boxes. The model uses so-called object queries to detect objects in an image. Each object query looks for a particular object in the image. For COCO, the number of object queries is set to 100. 

The model is trained using a "bipartite matching loss": one compares the predicted classes + bounding boxes of each of the N = 100 object queries to the ground truth annotations, padded up to the same length N (so if an image only contains 4 objects, 96 annotations will just have a "no object" as class and "no bounding box" as bounding box). The Hungarian matching algorithm is used to create an optimal one-to-one mapping between each of the N queries and each of the N annotations. Next, standard cross-entropy (for the classes) and a linear combination of the L1 and generalized IoU loss (for the bounding boxes) are used to optimize the parameters of the model.

DETR can be naturally extended to perform panoptic segmentation, by adding a mask head on top of the decoder outputs.

## Intended uses & limitations

You can use the raw model for panoptic segmentation. See the [model hub](https://huggingface.co/models?search=facebook/detr) to look for all available DETR models.

### How to use

Here is how to use this model:

```python
from transformers import DetrFeatureExtractor, DetrForSegmentation
from PIL import Image
import requests

url = 'http://images.cocodataset.org/val2017/000000039769.jpg'
image = Image.open(requests.get(url, stream=True).raw)

feature_extractor = DetrFeatureExtractor.from_pretrained('facebook/detr-resnet-101-panoptic')
model = DetrForSegmentation.from_pretrained('facebook/detr-resnet-101-panoptic')

inputs = feature_extractor(images=image, return_tensors="pt")
outputs = model(**inputs)
# model predicts COCO classes, bounding boxes, and masks
logits = outputs.logits
bboxes = outputs.pred_boxes
masks = outputs.pred_masks
```

Currently, both the feature extractor and model support PyTorch. 

## Training data

The DETR model was trained on [COCO 2017 panoptic](https://cocodataset.org/#download), a dataset consisting of 118k/5k annotated images for training/validation respectively. 

## Training procedure

### Preprocessing

The exact details of preprocessing of images during training/validation can be found [here](https://github.com/facebookresearch/detr/blob/master/datasets/coco_panoptic.py). 

Images are resized/rescaled such that the shortest side is at least 800 pixels and the largest side at most 1333 pixels, and normalized across the RGB channels with the ImageNet mean (0.485, 0.456, 0.406) and standard deviation (0.229, 0.224, 0.225).

### Training

The model was trained for 300 epochs on 16 V100 GPUs. This takes 3 days, with 4 images per GPU (hence a total batch size of 64).

## Evaluation results

This model achieves the following results on COCO 2017 validation: a box AP (average precision) of **40.1**, a segmentation AP (average precision) of **33** and a PQ (panoptic quality) of **45.1**.

For more details regarding evaluation results, we refer to table 5 of the original paper.

### BibTeX entry and citation info

```bibtex
@article{DBLP:journals/corr/abs-2005-12872,
  author    = {Nicolas Carion and
               Francisco Massa and
               Gabriel Synnaeve and
               Nicolas Usunier and
               Alexander Kirillov and
               Sergey Zagoruyko},
  title     = {End-to-End Object Detection with Transformers},
  journal   = {CoRR},
  volume    = {abs/2005.12872},
  year      = {2020},
  url       = {https://arxiv.org/abs/2005.12872},
  archivePrefix = {arXiv},
  eprint    = {2005.12872},
  timestamp = {Thu, 28 May 2020 17:38:09 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2005-12872.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```