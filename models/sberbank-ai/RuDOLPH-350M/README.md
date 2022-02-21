# RuDOLPH-350M (Medium)

RuDOLPH: One Hyper-Modal Transformer can be creative as DALL-E and smart as CLIP

<img src="https://raw.githubusercontent.com/sberbank-ai/ru-dolph/master/pics/rudolph-generated.png" height="60" border="2"/>


Model was trained by [Sber AI](https://github.com/sberbank-ai) and [SberDevices](https://sberdevices.ru/) teams.  
* Task: `text2image generation`; `self reranking`; `text ranking`; `image ranking`; `image2text generation`; `zero-shot image classification`, `text2text generation`;
* Language: `Russian`
* Type: `encoder-decoder`
* Num Parameters: `350M`
* Training Data Volume: `156 million text-image pairs`


# Model Description

**Ru**ssian **D**iffusion **O**n **L**anguage **P**icture **H**yper-modality (RuDOLPH) 350M is a fast and light text-image-text transformer (350M GPT-3) designed for a quick and easy fine-tuning setup for the solution of various tasks: from generating images by text description and image classification to visual question answering and more. This model demonstrates the power of Hyper-modality Transformers.

*(!!!) Hyper-modality means generalized multi-modal, e.g., model that consists of two multi-modal parts: text-2-image and image-2-text becomes text and image hyper-modality model*

# Sparse Attention Mask

The primary proposed method is to modify the sparse transformer's attention mask to better control multi-modalities and up to the next level with "hyper-modality". It allows us to calculate the transitions of modalities in both directions, unlike another similar work DALL-E Transformer, which used only one direction, "text to image". The proposed "image to right text" direction is achieved by extension sparse attention mask to the right for auto-repressively text generation with image condition without attention to left text.

<img src="https://raw.githubusercontent.com/sberbank-ai/ru-dolph/master/pics/attention_masks.png" height="40" border="2"/>

# Authors

+ Alex Shonenkov: [Github](https://github.com/shonenkov), [Kaggle GM](https://www.kaggle.com/shonenkov)
+ Michael Konstantinov: [Mishin Learning](https://t.me/mishin_learning), [Transformer Community](https://transformer.community/)
