---
language: id
---

# Image-captioning-Indonesia

This is an encoder-decoder image captioning model using [CLIP](https://huggingface.co/transformers/model_doc/clip.html) as the visual encoder and [Marian](https://huggingface.co/transformers/model_doc/marian.html) as the textual decoder on datasets with Indonesian captions.

This model was trained using HuggingFace's Flax framework and is part of the [JAX/Flax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organized by [HuggingFace](https://huggingface.co). All training was done on a TPUv3-8 VM sponsored by the Google Cloud team.

## How to use
At time of writing, you will need to install [HuggingFace](https://github.com/huggingface/) from its latest master branch in order to load `FlaxMarian`.

You will also need to have the [`flax_clip_vision_marian` folder](https://github.com/indonesian-nlp/Indonesia-Image-Captioning/tree/main/flax_clip_vision_marian) in your project directory to load the model using the `FlaxCLIPVisionMarianForConditionalGeneration` class.

```python
from torchvision.io import ImageReadMode, read_image
from torchvision.transforms import CenterCrop, ConvertImageDtype, Normalize, Resize
from torchvision.transforms.functional import InterpolationMode

import torch
import numpy as np
from transformers import MarianTokenizer
from flax_clip_vision_marian.modeling_clip_vision_marian import FlaxCLIPVisionMarianForConditionalGeneration

clip_marian_model_name = 'flax-community/Image-captioning-Indonesia'
model = FlaxCLIPVisionMarianForConditionalGeneration.from_pretrained(clip_marian_model_name)

marian_model_name = 'Helsinki-NLP/opus-mt-en-id'
tokenizer = MarianTokenizer.from_pretrained(marian_model_name)

config = model.config
image_size = config.clip_vision_config.image_size

# Image transformation
transforms = torch.nn.Sequential(
                    Resize([image_size], interpolation=InterpolationMode.BICUBIC),
                    CenterCrop(image_size),
                    ConvertImageDtype(torch.float),
                    Normalize((0.48145466, 0.4578275, 0.40821073), (0.26862954, 0.26130258, 0.27577711)),
                )

# Hyperparameters
max_length = 8
num_beams = 4
gen_kwargs = {"max_length": max_length, "num_beams": num_beams}

def generate_step(batch):
    output_ids = model.generate(pixel_values, **gen_kwargs)
    token_ids = np.array(output_ids.sequences)[0]
    caption = tokenizer.decode(token_ids)
    return caption

image_file_path = image_file_path
image = read_image(image_file_path, mode=ImageReadMode.RGB)
image = transforms(image)
pixel_values = torch.stack([image]).permute(0, 2, 3, 1).numpy()

generated_ids = generate_step(pixel_values)

print(generated_ids)
```

## Training data
The Model was trained on translated Coco,Flickr and ViZWiz, each of them were translated using google translate and marian mt. we took only random 2 captions per image for each datasets

## Training procedure 
The model was trained on a TPUv3-8 VM provided by the Google Cloud team.

## Team members
- Cahya Wirawan ([@cahya](https://huggingface.co/cahya))
- Galuh Sahid ([@Galuh](https://huggingface.co/Galuh))
- Muhammad Agung Hambali ([@AyameRushia](https://huggingface.co/AyameRushia))
- Samsul Rahmadani ([@munggok](https://huggingface.co/munggok))