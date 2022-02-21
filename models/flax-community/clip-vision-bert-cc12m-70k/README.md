# CLIP-Vision-BERT Multilingual Pre-trained Model

Pretrained CLIP-Vision-BERT pre-trained on translated [Conceptual-12M](https://github.com/google-research-datasets/conceptual-12m) image-text pairs using a masked language modeling (MLM) objective. 10M cleaned image-text pairs are translated using [mBART-50 one-to-many model](https://huggingface.co/facebook/mbart-large-50-one-to-many-mmt) to 2.5M examples each in English, French, German and Spanish. This model is based on the VisualBERT which was introduced in
[this paper](https://arxiv.org/abs/1908.03557) and first released in
[this repository](https://github.com/uclanlp/visualbert). We trained CLIP-Vision-BERT model during community week hosted by Huggingface 🤗 using JAX/Flax.

This checkpoint is pre-trained for 70k steps.

## Model description
CLIP-Vision-BERT is a modified BERT model which takes in visual embeddings from CLIP-Vision transformer and concatenates them with BERT textual embeddings before passing them to the self-attention layers of BERT. This is done for deep cross-modal interaction between the two modes.

## Intended uses & limitations❗️
You can use the raw model for masked language modeling, but it's mostly intended to be fine-tuned on a downstream task.
Note that this model is primarily aimed at being fine-tuned on tasks such as visuo-linguistic sequence classification or visual question answering. We used this model to fine-tuned on a multi-translated version of the visual question answering task - [VQA v2](https://visualqa.org/challenge.html). Since Conceptual-12M is a dataset scraped from the internet, it will involve some biases which will also affect all fine-tuned versions of this model.

### How to use❓
You can use this model directly with a pipeline for masked language modeling. You will need to clone the model from [here](https://github.com/gchhablani/multilingual-vqa). An example of usage is shown below:
```python
>>> from torchvision.io import read_image
>>> import numpy as  np
>>> import os
>>> from transformers import CLIPProcessor, BertTokenizerFast
>>> from model.flax_clip_vision_bert.modeling_clip_vision_bert import FlaxCLIPVisionBertForMaskedLM
>>> image_path = os.path.join('images/val2014', os.listdir('images/val2014')[0])
>>> img = read_image(image_path)
>>> clip_processor = CLIPProcessor.from_pretrained('openai/clip-vit-base-patch32')
ftfy or spacy is not installed using BERT BasicTokenizer instead of ftfy.
>>> clip_outputs = clip_processor(images=img)
>>> clip_outputs['pixel_values'][0] = clip_outputs['pixel_values'][0].transpose(1,2,0) # Need to transpose images as model expected channel last images.
>>> tokenizer = BertTokenizerFast.from_pretrained('bert-base-multilingual-uncased')
>>> model = FlaxCLIPVisionBertForMaskedLM.from_pretrained('flax-community/clip-vision-bert-cc12m-70k')
>>> text = "Three teddy [MASK] in a showcase."
>>> tokens = tokenizer([text], return_tensors="np")
>>> pixel_values = np.concatenate([clip_outputs['pixel_values']])
>>> outputs = model(pixel_values=pixel_values, **tokens)
>>> indices = np.where(tokens['input_ids']==tokenizer.mask_token_id)
>>> preds = outputs.logits[indices][0]
>>> sorted_indices = np.argsort(preds)[::-1] # Get reverse sorted scores
>>> top_5_indices = sorted_indices[:5]
>>> top_5_tokens = tokenizer.convert_ids_to_tokens(top_5_indices)
>>> top_5_scores = preds[top_5_indices]
>>> print(dict(zip(top_5_tokens, top_5_scores)))
{'bears': 19.400345, 'bear': 17.866995, 'animals': 14.453735, 'dogs': 14.427426, 'girls': 14.097499}
```

## Training data 🏋🏻‍♂️
The CLIP-Vision-BERT model was pre-trained on a translated version of the Conceptual-12m dataset in four languages using mBART-50: English, French, German and Spanish, with 2.5M image-text pairs in each.

The dataset captions and image urls can be downloaded from [flax-community/conceptual-12m-mbart-50-translated](https://huggingface.co/datasets/flax-community/conceptual-12m-mbart-50-multilingual).

## Data Cleaning 🧹

Though the original dataset contains 12M image-text pairs, a lot of the URLs are invalid now, and in some cases, images are corrupt or broken. We remove such examples from our data, which leaves us with approximately 10M image-text pairs.

**Splits**
We used 99% of the 10M examples as a train set, and the remaining ~ 100K examples as our validation set. 

## Training procedure 👨🏻‍💻
### Preprocessing
The texts are lowercased and tokenized using WordPiece and a shared vocabulary size of approximately 110,000. The beginning of a new document is marked with `[CLS]` and the end of one by `[CLS]`
The details of the masking procedure for each sentence are the following:
- 15% of the tokens are masked.
- In 80% of the cases, the masked tokens are replaced by `[MASK]`.
- In 10% of the cases, the masked tokens are replaced by a random token (different) from the one they replace.
- In the 10% remaining cases, the masked tokens are left as is.


The visual embeddings are taken from the CLIP-Vision model and combined with the textual embeddings inside the BERT embedding layer. The padding is done in the middle. Here is an example of what the embeddings look like:

```
[CLS Emb] [Textual Embs] [SEP Emb] [Pad Embs] [Visual Embs]
```

A total length of 128 tokens, including the visual embeddings, is used. The texts are truncated or padded accordingly. 

### Pretraining
The checkpoint of the model was trained on Google Cloud Engine TPUv3-8 machine (with 335 GB of RAM, 1000 GB of hard drive, 96 CPU cores) **8 v3 TPU cores** for 70k steps with a per device batch size of 64 and a max sequence length of 128. The optimizer used is Adafactor with a learning rate of 1e-4, learning rate warmup for 1,000 steps, and linear decay of the learning rate after.

We tracked experiments using TensorBoard. Here is the link to the main dashboard: [CLIP Vision BERT CC12M Pre-training Dashboard](https://huggingface.co/flax-community/multilingual-vqa-pt-ckpts/tensorboard)


#### **Pretraining Results 📊**

The model at this checkpoint reached **eval accuracy of 67.85%** and **with train loss at 1.756 and eval loss at 1.706**.

## Team Members
  - Gunjan Chhablani [@gchhablani](https://hf.co/gchhablani)
  - Bhavitvya Malik[@bhavitvyamalik](https://hf.co/bhavitvyamalik)

## Acknowledgements
  We thank [Nilakshan Kunananthaseelan](https://huggingface.co/knilakshan20) for helping us whenever he could get a chance. We also thank [Abheesht Sharma](https://huggingface.co/abheesht) for helping in the discussions in the initial phases. [Luke Melas](https://github.com/lukemelas) helped us get the CC-12M data on our TPU-VMs and we are very grateful to him.

  This project would not be possible without the help of [Patrick](https://huggingface.co/patrickvonplaten) and [Suraj](https://huggingface.co/valhalla) who met with us frequently and helped review our approach and guided us throughout the project.

  Huge thanks to Huggingface 🤗 & Google Jax/Flax team for such a wonderful community week and for answering our queries on the Slack channel, and for providing us with the TPU-VMs.

<img src=https://pbs.twimg.com/media/E443fPjX0AY1BsR.jpg:large>
