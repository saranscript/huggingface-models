## VQGAN-f16-16384

### Model Description

This is a Pytorch Lightning checkpoint of VQGAN, which learns a codebook of context-rich visual parts by leveraging both the use of convolutional methods and transformers. It was introduced in [Taming Transformers for High-Resolution Image Synthesis](https://compvis.github.io/taming-transformers/) ([CVPR paper](https://openaccess.thecvf.com/content/CVPR2021/html/Esser_Taming_Transformers_for_High-Resolution_Image_Synthesis_CVPR_2021_paper.html)).

The model allows the encoding of images as a fixed-length sequence of tokens taken from the codebook.

This version of the model uses a reduction factor `f=16` and a vocabulary of `13,384` tokens.

As an example of how the reduction factor works, images of size `256x256` are encoded to sequences of `256` tokens: `256/16 * 256/16`. Images of `512x512` would result in sequences of `1024` tokens.

### Datasets Used for Training

* ImageNet. We didn't train this model from scratch. Instead, we started from [a checkpoint pre-trained on ImageNet](https://heibox.uni-heidelberg.de/d/a7530b09fed84f80a887/).
* [Conceptual Captions 3M](https://ai.google.com/research/ConceptualCaptions/) (CC3M).
* [OpenAI subset of YFCC100M](https://github.com/openai/CLIP/blob/main/data/yfcc100m.md).

We fine-tuned on CC3M and YFCC100M to improve the encoding quality of people and faces, which are not very well represented in ImageNet. We used a subset of 2,268,720 images from CC3M and YFCC100M for this purpose.

### Training Process

Finetuning was performed in PyTorch using [taming-transformers](https://github.com/CompVis/taming-transformers). The full training process and model preparation includes these steps:

* Pre-training on ImageNet. Previously performed. We used [this checkpoint](https://heibox.uni-heidelberg.de/d/a7530b09fed84f80a887).
* Fine-tuning, [Part 1](https://wandb.ai/wandb/hf-flax-dalle-mini/runs/2021-07-09T15-33-11_dalle_vqgan?workspace=user-borisd13).
* Fine-tuning, [Part 2](https://wandb.ai/wandb/hf-flax-dalle-mini/runs/2021-07-09T21-42-07_dalle_vqgan?workspace=user-borisd13) – continuation from Part 1. The final checkpoint has been logged as an artifact in the training run and is the model present in this card.
* Conversion to JAX as [`flax-community/vqgan_f16_16384`](https://huggingface.co/flax-community/vqgan_f16_16384).

### How to Use

The checkpoint can be loaded using Pytorch-Lightning.

Note: `omegaconf==2.0.0` is required for loading the checkpoint.

### Related Models in the Hub

* JAX version of VQGAN, trained on the same datasets described here: [`flax-community/vqgan_f16_16384`](https://huggingface.co/flax-community/vqgan_f16_16384).
* [DALL·E mini](https://huggingface.co/flax-community/dalle-mini), a Flax/JAX simplified implementation of OpenAI's DALL·E.

### Other

This model was successfully used as part of the implementation of [DALL·E mini](https://github.com/borisdayma/dalle-mini). Our [report](https://wandb.ai/dalle-mini/dalle-mini/reports/DALL-E-mini--Vmlldzo4NjIxODA) contains more details on how to leverage it in an image encoding / generation pipeline.
