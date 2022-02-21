---
language: en
license: mit
datasets:
- web crawled (coming soon)
---

# Simple CNN-based Artist Classifier

This repo contains a simple CNN-based Keras model which classifies images into one of 10 selected artists/painters.

- The purpose of this model was for a quick prototyping
- Data has been web-crawled using `https://github.com/YoongiKim/AutoCrawler`
- 10 popular artists/painters were chosen:
    - \[ARTIST\]: \[ID\]
    - claude_monet: 0,
    - henri_matisse: 1,
    - jean_michel_basquiat: 2,
    - keith_haring: 3,
    - pablo_picasso: 4,
    - pierre_augste_renoir: 5,
    - rene_magritte: 6,
    - roy_richtenstein: 7,
    - vincent_van_gogh: 8,
    - wassily_kandinsky: 9
- About 100 representative paintings per artist were crawled and manually checked
- Dataset will be shared later

# How to use
```python
import tensorflow as tf
from huggingface_hub import from_pretrained_keras
model = from_pretrained_keras("jkang/drawing-artist-classifier")

image_file = 'monet.jpg'
img = tf.io.read_file(image_file)
img = tf.io.decode_jpeg(img, channels=3)

last_layer_activation, predictions = model(img[tf.newaxis,...])
```

# Intended uses & limitations
You can use this model freely for predicting artists or trends of a given image.
Please keep in mind that this model is not intended for production, but for research and quick prototyping.
Web-crawled image data might not have a balanced amount of drawings that sufficiently represent the artists.
---
- 2022-01-18 first created by jaekoo kang