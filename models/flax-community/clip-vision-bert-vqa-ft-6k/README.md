# CLIP-Vision-BERT Multilingual VQA Model

Fine-tuned CLIP-Vision-BERT on translated [VQAv2](https://visualqa.org/challenge.html) image-text pairs using sequence classification objective. We translate the dataset to three other languages other than English: French, German, and Spanish using the [MarianMT Models](https://huggingface.co/transformers/model_doc/marian.html). This model is based on the VisualBERT which was introduced in
[this paper](https://arxiv.org/abs/1908.03557) and first released in
[this repository](https://github.com/uclanlp/visualbert). The output is 3129 class logits, the same classes as used by VisualBERT authors. 

The initial weights are loaded from the Conceptual-12M 60k [checkpoints](https://huggingface.co/flax-community/clip-vision-bert-cc12m-60k).

We trained the CLIP-Vision-BERT VQA model during community week hosted by Huggingface 🤗 using JAX/Flax.

## Model description
CLIP-Vision-BERT is a modified BERT model which takes in visual embeddings from the CLIP-Vision transformer and concatenates them with BERT textual embeddings before passing them to the self-attention layers of BERT. This is done for deep cross-modal interaction between the two modes.

## Intended uses & limitations❗️
This model is fine-tuned on a multi-translated version of the visual question answering task - [VQA v2](https://visualqa.org/challenge.html). Since VQAv2 is a dataset scraped from the internet, it will involve some biases which will also affect all fine-tuned versions of this model.

### How to use❓
You can use this model directly on visual question answering. You will need to clone the model from [here](https://github.com/gchhablani/multilingual-vqa). An example of usage is shown below:

```python
>>> from torchvision.io import read_image
>>> import numpy as  np
>>> import os
>>> from transformers import CLIPProcessor, BertTokenizerFast
>>> from model.flax_clip_vision_bert.modeling_clip_vision_bert import FlaxCLIPVisionBertForSequenceClassification
>>> image_path = os.path.join('images/val2014', os.listdir('images/val2014')[0])
>>> img = read_image(image_path)
>>> clip_processor = CLIPProcessor.from_pretrained('openai/clip-vit-base-patch32')
ftfy or spacy is not installed using BERT BasicTokenizer instead of ftfy.
>>> clip_outputs = clip_processor(images=img)
>>> clip_outputs['pixel_values'][0] = clip_outputs['pixel_values'][0].transpose(1,2,0) # Need to transpose images as model expected channel last images.
>>> tokenizer = BertTokenizerFast.from_pretrained('bert-base-multilingual-uncased')
>>> model = FlaxCLIPVisionBertForSequenceClassification.from_pretrained('flax-community/clip-vision-bert-vqa-ft-6k')
>>> text = "Are there teddy bears in the image?"
>>> tokens = tokenizer([text], return_tensors="np")
>>> pixel_values = np.concatenate([clip_outputs['pixel_values']])
>>> outputs = model(pixel_values=pixel_values, **tokens)
>>> preds = outputs.logits[0]
>>> sorted_indices = np.argsort(preds)[::-1] # Get reverse sorted scores
>>> top_5_indices = sorted_indices[:5]
>>> top_5_tokens = list(map(model.config.id2label.get,top_5_indices))
>>> top_5_scores = preds[top_5_indices]
>>> print(dict(zip(top_5_tokens, top_5_scores)))
{'yes': 15.809224, 'no': 7.8785815, '<unk>': 4.622649, 'very': 4.511462, 'neither': 3.600822}
```

## Training data 🏋🏻‍♂️
The CLIP-Vision-BERT model was fine-tuned on the translated version of the VQAv2 dataset in four languages using Marian: English, French, German and Spanish. Hence, the dataset is four times the original English questions.

The dataset questions and image URLs/paths can be downloaded from [flax-community/multilingual-vqa](https://huggingface.co/datasets/flax-community/multilingual-vqa).

## Data Cleaning 🧹

Though the original dataset contains 443,757  train and 214,354 validation image-question pairs. We only use the `multiple_choice_answer`. The answers which are not present in the 3129 classes are mapped to the `<unk>` label.

**Splits**
We use the original train-val splits from the VQAv2 dataset. After translation, we get 1,775,028 train image-text pairs, and 857,416 validation image-text pairs.

## Training procedure 👨🏻‍💻
### Preprocessing
The texts are lowercased and tokenized using WordPiece and a shared vocabulary size of approximately 110,000. The beginning of a new document is marked with `[CLS]` and the end of one by `[SEP]`.

### Fine-tuning
The checkpoint of the model was trained on Google Cloud Engine TPUv3-8 machine (with 335 GB of RAM, 1000 GB of hard drive, 96 CPU cores) **8 v3 TPU cores** for 6k steps with a per device batch size of 128 and a max sequence length of 128. The optimizer used is AdamW with a learning rate of 5e-5, learning rate warmup for 1600 steps, and linear decay of the learning rate after.

We tracked experiments using TensorBoard. Here is link to main dashboard: [CLIP Vision BERT VQAv2 Fine-tuning Dashboard](https://huggingface.co/flax-community/multilingual-vqa-pt-60k-ft/tensorboard)


#### **Fine-tuning Results 📊**

The model at this checkpoint reached **eval accuracy of 0.49** on our multilingual VQAv2 dataset.


## Team Members
  - Gunjan Chhablani [@gchhablani](https://hf.co/gchhablani)
  - Bhavitvya Malik[@bhavitvyamalik](https://hf.co/bhavitvyamalik)

## Acknowledgements
  We thank [Nilakshan Kunananthaseelan](https://huggingface.co/knilakshan20) for helping us whenever he could get a chance. We also thank [Abheesht Sharma](https://huggingface.co/abheesht) for helping in the discussions in the initial phases. [Luke Melas](https://github.com/lukemelas) helped us get the CC-12M data on our TPU-VMs and we are very grateful to him.

  This project would not be possible without the help of [Patrick](https://huggingface.co/patrickvonplaten) and [Suraj](https://huggingface.co/valhalla) who met with us frequently and helped review our approach and guided us throughout the project.

  Huge thanks to Huggingface 🤗 & Google Jax/Flax team for such a wonderful community week and for answering our queries on the Slack channel, and for providing us with the TPU-VMs.

<img src=https://pbs.twimg.com/media/E443fPjX0AY1BsR.jpg:large>