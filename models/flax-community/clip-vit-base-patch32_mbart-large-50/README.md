# CLIP-Vision-mBART50 Seq2Seq Encoder-Decoder Model

Pretrained CLIP-Vision-mBART50 pre-trained on subset of translated Conceptual-12M image-text pairs using a seq2seq model training objective. 2.5M cleaned English image-text pairs are translated using Marian Model for respective languages to 2.5M examples each in English, French, German and Spanish. We trained CLIP-Vision-mBART50 model during community week hosted by Huggingface 🤗 using JAX/Flax.

## Model description
CLIP-Vision-mBART50 is a modified transformers model which takes in visual embeddings from CLIP-Vision transformer and feeds into the `encoder_hidden_states` of a mBART50 decoder. This is done for deep cross-modal interaction via `cross-attention` between the two modes. The decoder then predicts logits for the `input_ids` provided and can be used for generation.

## Intended uses & limitations❗️
You can use the raw model for encoder decoder network where you want the encoder to encode images and decoder to decode text.

Note that this model is primarily aimed at being fine-tuned on tasks like multi-lingual/mono-lingual image captioning.

### How to use❓
You will need to clone the model from [here](https://github.com/gchhablani/multilingual-image-captioning). An example of usage is shown below:
```python
from torchvision.io import read_image
import numpy as  np
import os, wget
from transformers import CLIPProcessor, MBart50TokenizerFast
from model.flax_clip_vision_mbart.modeling_clip_vision_mbart import FlaxCLIPVisionMBartForConditionalGeneration
img = wget("http://images.cocodataset.org/val2017/000000397133.jpg")
img = read_image(img) # reading image
clip_processor = CLIPProcessor.from_pretrained('openai/clip-vit-base-patch32')
clip_outputs = clip_processor(images=img)
clip_outputs['pixel_values'][0] = clip_outputs['pixel_values'][0].transpose(1,2,0) # Need to transpose images as model expected channel last images.
tokenizer = MBart50TokenizerFast.from_pretrained('facebook/mbart-large-50"')
model = FlaxCLIPVisionBertForMaskedLM.from_pretrained('flax-community/clip-vit-base-patch32_mbart-large-50')
output_ids = model.generate(batch["pixel_values"], forced_bos_token_id=tokenizer.lang_code_to_id["es_XX"], num_beams=4, max_length=64).sequences  # "es_XX is the language code in which you want the translation
# en_XX: English, fr_XX: French, es_XX: Spanish, de_DE: Deutsch
output_string = tokenizer.batch_decode(output_ids.reshape(-1, 64), skip_special_tokens=True, max_length=64)
output_string  # Un restaurante u otro lugar para comer en el Hotel
```

## Training data 🏋🏻‍♂️
The Multi-lingual image captioning model was trained on a subset of Conceptual 12M dataset by Google:
<br>
<br>
[Conceptual 12M](https://github.com/google-research-datasets/conceptual-12m), Introduced by Changpinyo et al. in [Conceptual 12M: Pushing Web-Scale Image-Text Pre-Training To Recognize Long-Tail Visual Concepts](https://arxiv.org/abs/2102.08981).

The translated dataset can be downloaded from [conceptual-12m-multilingual-marian](https://huggingface.co/datasets/flax-community/conceptual-12m-multilingual-marian). We do not provide images as we do not own any of them. One can download images from the `image_url` section of the original Conceptual 12M dataset.

## Data Cleaning 🧹
Though the original dataset contains 12M image-text pairs, a lot of the URLs are invalid now, and in some cases, images are corrupt or broken. We remove such examples from our data, which leaves us with approximately 10M image-text pairs.

#### **Train set:**
Total data: 10010625 captions, 2502656 images <br>

Language-wise captions distribution: <br>
English: 2502656<br>
Spanish: 2502656<br>
Deutsch: 2502656<br>
French: 2502656<br>

#### **Validation set**
Total data: 110592 captions, 27648 images <br>

Language-wise captions distribution: <br>
English: 27648<br>
Spanish: 27648<br>
Deutsch: 27648<br>
French: 27648<br>

## Training procedure 👨🏻‍💻
### Training
The model was trained on Google Cloud Engine TPUv3-8 machine (with 335 GB of RAM, 1000 GB of hard drive, 96 CPU cores) **8 v3 TPU cores** for 42K steps with a batch size of 128 and a sequence length of 128. The
optimizer used is Adam with a learning rate of 3e-4, β1 = 0.9, β2 = 0.98 and
ε = 1e-8, a weight decay of 0.01, learning rate warmup for 1,000 steps and linear decay of the learning
rate after.

We tracked experiments using Tensorboard which can be found in `Training Metrics` tab. BLEU scores for languages other than English might be wrongly tracked but the model gives good performance in other languages too as evident from the evaluation scores.

#### **Pretraining Results 📊**

Our model reached **eval loss of ~2.6** around ~60k steps. Here are the BLEU scores (out of 1) for different languages:

|Language                  |BLEU-1|BLEU-2|BLEU-3|BLEU-4|
|--------------------------|------|------|------|------|
|English                   | 0.13083| 0.08887| 0.06681 | 0.04899|
|Spanish                   | 0.15981| 0.09858| 0.06918| 0.04776|
|German                    | 0.14234| 0.09817| 0.07405| 0.0515|
|French                    | 0.13021| 0.08862| 0.06598| 0.04647|

Model used: ckpt-51999/

In order to reproduce the results, one can use the [evaluation script](https://github.com/gchhablani/multilingual-image-captioning/blob/main/evaluation.py) available in this project's repository.

## **App Demo**

You can try out our model on 🤗 Huggingface's spaces 🪐 :
[Streamlit app of Multi-lingual Image Captioning model on Huggingface Spaces](https://huggingface.co/spaces/flax-community/multilingual-image-captioning)


## Team Members
  - Bhavitvya Malik [@bhavitvyamalik](https://github.com/bhavitvyamalik)
  - Gunjan Chhablani [@gchhablani](https://github.com/gchhablani)

## Credits
  Thanks to Huggingface 🤗 & Google JAX/FLAX team for such a wonderful community week. Big thanks to [@patrickvonplaten](https://github.com/patrickvonplaten) and [@patil-suraj](https://github.com/patil-suraj) for helping us with our solution during the community week.

<img src=https://pbs.twimg.com/media/E443fPjX0AY1BsR.jpg:large>
