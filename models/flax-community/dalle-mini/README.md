---
language:
- en
pipeline_tag: text-to-image
inference: false
---

## DALL·E mini - Generate images from text

<img style="text-align:center; display:block;" src="https://raw.githubusercontent.com/borisdayma/dalle-mini/main/img/logo.png" width="200">

* [Technical Report](https://wandb.ai/dalle-mini/dalle-mini/reports/DALL-E-mini--Vmlldzo4NjIxODA)
* [Demo](https://huggingface.co/spaces/flax-community/dalle-mini)

### Model Description

This is an attempt to replicate OpenAI's [DALL·E](https://openai.com/blog/dall-e/), a model capable of generating arbitrary images from a text prompt that describes the desired result. 

![DALL·E mini demo screenshot](img/demo_screenshot.png)

This model's architecture is a simplification of the original, and leverages previous open source efforts and available pre-trained models. Results have lower quality than OpenAI's, but the model can be trained and used on less demanding hardware. Our training was performed on a single TPU v3-8 for a few days.

### Components of the Architecture

The system relies on the Flax/JAX infrastructure, which are ideal for TPU training. TPUs are not required, both Flax and JAX run very efficiently on GPU backends.

The main components of the architecture include:

* An encoder, based on [BART](https://arxiv.org/abs/1910.13461). The encoder transforms a sequence of input text tokens to a sequence of image tokens. The input tokens are extracted from the text prompt by using the model's tokenizer. The image tokens are a fixed-length sequence, and they represent indices in a VQGAN-based pre-trained codebook.

* A decoder, which converts the image tokens to image pixels. As mentioned above, the decoder is based on a [VQGAN model](https://compvis.github.io/taming-transformers/).

The model definition we use for the encoder can be downloaded from our [Github repo](https://github.com/borisdayma/dalle-mini). The encoder is represented by the class `CustomFlaxBartForConditionalGeneration`.

To use the decoder, you need to follow the instructions in our accompanying VQGAN model in the hub, [flax-community/vqgan_f16_16384](https://huggingface.co/flax-community/vqgan_f16_16384).

### How to Use

The easiest way to get familiar with the code and the models is to follow the inference notebook we provide in our [github repo](https://github.com/borisdayma/dalle-mini/blob/main/dev/inference/inference_pipeline.ipynb). For your convenience, you can open it in Google Colaboratory: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/borisdayma/dalle-mini/blob/main/dev/inference/inference_pipeline.ipynb)

If you just want to test the trained model and see what it comes up with, please visit [our demo](https://huggingface.co/spaces/flax-community/dalle-mini), available in 🤗 Spaces.

### Additional Details

Our [report](https://wandb.ai/dalle-mini/dalle-mini/reports/DALL-E-mini--Vmlldzo4NjIxODA) contains more details about how the model was trained and shows many examples that demonstrate its capabilities.
