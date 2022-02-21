## Acknowledgement
Google supported this work by providing Google Cloud credit. Thank you Google for supporting the open source! 🎉

## What is this?
This model is a finetuned version of [dbmdz/distilbert-base-turkish-cased](https://huggingface.co/dbmdz/distilbert-base-turkish-cased) to be used as a text encoder in Turkish with [CLIP](https://github.com/openai/CLIP)'s `ViT-B/32` image encoder. It should be used with `clip_head.h5` from [my accompanying repo on GitHub]. Go to that repo for fully working example, and a simple usage example is as follows:

```python
from transformers import AutoTokenizer, TFAutoModel
import tensorflow as tf
import numpy as np
from PIL import Image
import torch
import clip

model_name = "mys/distilbert-base-turkish-cased-clip"
base_model = TFAutoModel.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)
head_model = tf.keras.models.load_model("./clip_head.h5")

def encode_text(base_model, tokenizer, head_model, texts):
    tokens = tokenizer(texts, padding=True, return_tensors='tf')
    embs = base_model(**tokens)[0]

    attention_masks = tf.cast(tokens['attention_mask'], tf.float32)
    sample_length = tf.reduce_sum(attention_masks, axis=-1, keepdims=True)
    masked_embs = embs * tf.expand_dims(attention_masks, axis=-1)
    base_embs = tf.reduce_sum(masked_embs, axis=1) / tf.cast(sample_length, tf.float32)
    clip_embs = head_model(base_embs)
    clip_embs /= tf.norm(clip_embs, axis=-1, keepdims=True)
    return clip_embs



demo_images = {
    "bilgisayarda çalışan bir insan": "myspc.jpeg",
    "sahilde bir insan ve bir heykel": "mysdk.jpeg"
    }

clip_model, preprocess = clip.load("ViT-B/32")
images = {key: Image.open(f"images/{value}") for key, value in demo_images.items()}
img_inputs = torch.stack([preprocess(image).to('cpu') for image in images.values()])

with torch.no_grad():
    image_embs = clip_model.encode_image(img_inputs).float().to('cpu')

image_embs /= image_embs.norm(dim=-1, keepdim=True)
image_embs = image_embs.detach().numpy()
text_embs = encode_text(base_model, tokenizer, head_model, list(images.keys())).numpy()
similarities = image_embs @ text_embs.T
logits = tf.nn.softmax(tf.convert_to_tensor(similarities)).numpy()
idxs = np.argmax(logits, axis=-1).tolist()
for i, (key, value) in enumerate(demo_images.items()):
    print("path: ", value, "true label: ", key, "prediction: ", list(demo_images.keys())[idxs[i]], "score: ", logits[i, idxs[i]])
```

Sample images referred in the code snippet above can be found under `images` directory in the gitHub repo.

## How it works
`encode_text()` function agregates per-token hidden states outputted by the Distilbert model to produce a single vector per sequence. Then, `clip_head.h5` model projects this vector onto the same vector space as CLIP's text encoder with a single dense layer. First, all the Distilbert layers were frozen an and the head dense layer was trained for a few epochs. Then, freezing was removed and the dense layer was trained with the Distilbert layers for a few more epochs. I created the dataset by machine-translating COCO captions into Turkish. During training, vector representations of English captions outputted by the original CLIP text encoder was used as target values, and MSE between these vectors and `clip_head.h5` outputs were minimized.

## Dataset
The dataset and the training notebook will be released soon.