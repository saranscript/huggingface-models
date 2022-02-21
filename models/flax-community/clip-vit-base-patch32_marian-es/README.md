# CLIP-Vision-Marian Seq2Seq Encoder-Decoder Model

Pretrained CLIP-Vision-Marian pre-trained on a subset of Spanish-translated Conceptual-12M image-text pairs using a seq2seq model training objective. 2.5M cleaned English image-text pairs are translated using Spanish Marian Model. We trained CLIP-Vision-Marian model during community week hosted by Huggingface 🤗 using JAX/Flax.

## Model description
CLIP-Vision-Marian is a modified transformers model which takes in visual embeddings from CLIP-Vision transformer and feeds into the `encoder_hidden_states` of a Marian decoder. This is done for deep cross-modal interaction via `cross-attention` between the two modes. The decoder then predicts logits for the `input_ids` provided and can be used for generation.

## Intended uses & limitations❗️
You can use the raw model for encoder-decoder network where you want the encoder to encode images and the decoder to decode text.

Note that this model is primarily aimed at being fine-tuned on tasks like Spanish image captioning.

### How to use❓
You will need to clone the model from [here](https://github.com/bhavitvyamalik/spanish-image-captioning). An example of usage is shown below:
```python
>>> from torchvision.io import read_image
>>> import numpy as  np
>>> import wget
>>> import os
>>> from transformers import CLIPProcessor, MarianTokenizer
>>> from models.flax_clip_vision_marian.modeling_clip_vision_marian import FlaxCLIPVisionMarianMT
img = wget.download("https://huggingface.co/streamlitiframe/flax-community/spanish-image-captioning/+/media/55a8898e61131569cc0ed4e72a8b3092969d63c2dff4f47ed9ef0d89.jpeg")
>>> img = read_image(img) # reading image
>>> clip_processor = CLIPProcessor.from_pretrained('flax-community/clip-vit-base-patch32_marian')
>>> clip_outputs = clip_processor(images=img)
>>> clip_outputs['pixel_values'][0] = clip_outputs['pixel_values'][0].transpose(1,2,0) # Need to transpose images as model expected channel last images.
>>> tokenizer = MarianTokenizer.from_pretrained('Helsinki-NLP/opus-mt-en-es')
>>> model = FlaxCLIPVisionMarianMT.from_pretrained('flax-community/clip-vit-base-patch32_marian-es')
>>> output_ids = model.generate(batch["pixel_values"], early_stopping=True, num_beams=4, max_length=64).sequences
>>> output_string = tokenizer.batch_decode(output_ids.reshape(-1, 64), skip_special_tokens=True, max_length=64)
>>> output_string
# Sopa de avena en un tazón blanco con arándanos frescos
```

## Training data 🏋🏻‍♂️
The Spanish image captioning model was trained on a subset of Conceptual 12M dataset by Google:
<br>
<br>
[Conceptual 12M](https://github.com/google-research-datasets/conceptual-12m), Introduced by Changpinyo et al. in [Conceptual 12M: Pushing Web-Scale Image-Text Pre-Training To Recognize Long-Tail Visual Concepts](https://arxiv.org/abs/2102.08981).

### Please update the dataset link here
The translated dataset can be downloaded from [conceptual-12m-multilingual-marian-es](https://huggingface.co/datasets/flax-community/conceptual-12m-multilingual-marian-es). We do not provide images as we do not own any of them. One can download images from the `image_url` section of the original Conceptual 12M dataset.

## Data Cleaning 🧹
Though the original dataset contains 12M image-text pairs, a lot of the URLs are invalid now, and in some cases, images are corrupt or broken. We remove such examples from our data, which leaves us with approximately 10M image-text pairs, out of which we took only 2.5M image, caption pairs.

#### **Train set:**
Total data: <br>
2475000 captions  <br>
2475000 images <br>

#### **Validation set**
Total data: <br>
25000 captions  <br>
25000 images <br>


## Training procedure 👨🏻‍💻
### Training
The model was trained on Google Cloud Engine TPUv3-8 machine (with 335 GB of RAM, 1000 GB of hard drive, 96 CPU cores) **8 v3 TPU cores** for 42K steps with a batch size of 128 and a sequence length of 128. The
optimizer used is Adam with a learning rate of 3e-4, β1 = 0.9, β2 = 0.98 and
ε = 1e-8, a weight decay of 0.01, learning rate warmup for 1,000 steps and linear decay of the learning
rate after.

We tracked experiments using Tensorboard which can be found in `Training Metrics` tab.

#### **Pretraining Results 📊**

Our model reached **eval loss of ~3.1** around ~20K steps. Here are the BLEU^ scores for different languages:

|Language                  |BLEU-1|BLEU-2|BLEU-3|BLEU-4|
|--------------------------|------|------|------|------|
|Spanish                   | 0.2015| 0.1348| 0.09982| 0.0748|

^BLEU scores are out of 1


## **App Demo**

You can try out our model on 🤗 Huggingface's spaces 🪐 :
[Streamlit app of Spanish Image Captioning model on Huggingface Spaces](https://huggingface.co/spaces/flax-community/spanish-image-captioning)


## Team Members
  - Bhavitvya Malik [@bhavitvyamalik](https://github.com/bhavitvyamalik)
  - Gunjan Chhablani [@gchhablani](https://github.com/gchhablani)

## Credits
  Thanks to Huggingface 🤗 & Google JAX/Flax team for such a wonderful community week. Big thanks to [@patrickvonplaten](https://github.com/patrickvonplaten) and [@patil-suraj](https://github.com/patil-suraj) for helping us with our solution during the community week.

<img src=https://pbs.twimg.com/media/E443fPjX0AY1BsR.jpg:large>
