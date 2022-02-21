---
tags:
- gan
- generative adversarial networks
- deep dream
license:
- cc0-1.0
---

## Keras Implementation of Deep Dream 🦚🌌

This repo contains the model and the notebook [for this Deep Dream implementation of Keras](https://keras.io/examples/generative/deep_dream/).

Full credits to: [François Chollet](https://twitter.com/fchollet)

 ![deepdream](https://keras.io/img/examples/generative/deep_dream/deep_dream_17_0.png)

## Background Information

 "Deep dream" is an image-filtering technique which consists of taking an image classification model, and running gradient ascent over an input image to try to maximize the activations of specific layers (and sometimes, specific units in specific layers) for this input. It produces hallucination-like visuals.

It was first introduced by Alexander Mordvintsev from Google in July 2015.

Process: 

- Load the original image.
- Define a number of processing scales ("octaves"), from smallest to largest.
- Resize the original image to the smallest scale.
- For every scale, starting with the smallest (i.e. current one): - Run gradient ascent - Upscale image to the next scale - Re-inject the detail that was lost at upscaling time
- Stop when we are back to the original size. To obtain the detail lost during upscaling, we simply take the original image, shrink it down, upscale it, and compare the result to the (resized) original image.
 