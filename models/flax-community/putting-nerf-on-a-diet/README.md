# Putting NeRF on a Diet: Semantically Consistent Few-Shot View Synthesis Implementation

[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://huggingface.co/spaces/flax-community/DietNerf-Demo) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1etYeMTntw5mh3FvJv4Ubb7XUoTtt5J9G?usp=sharing)

<p align="center"><img width="450" alt="스크린샷 2021-07-04 오후 4 11 51" src="https://user-images.githubusercontent.com/77657524/126361638-4aad58e8-4efb-4fc5-bf78-f53d03799e1e.png"></p>

This project attempted to implement the paper **[Putting NeRF on a Diet](https://arxiv.org/abs/2104.00677)** (DietNeRF) in JAX/Flax.
DietNeRF is designed for rendering quality novel views in few-shot learning scheme, a task that vanilla NeRF (Neural Radiance Field) struggles.
To achieve this, the author coins **Semantic Consistency Loss** to supervise DietNeRF by prior knowledge from CLIP Vision Transformer. Such supervision enables DietNeRF to learn 3D scene reconstruction with CLIP's prior knowledge on 2D views.  

Besides this repo, you can check our write-up and demo here:
- ✍️ **[Write-up in Notion](https://steep-cycle-f6b.notion.site/DietNeRF-Putting-NeRF-on-a-Diet-4aeddae95d054f1d91686f02bdb74745)**: more details of DietNeRF and our experiments
- ✨ **[Demo in Hugging Face Space](https://huggingface.co/spaces/flax-community/DietNerf-Demo)**: showcase our trained DietNeRFs by Streamlit

## 🤩 Demo
1. You can check out [our demo in Hugging Face Space](https://huggingface.co/spaces/flax-community/DietNerf-Demo)
2. Or you can set up our Streamlit demo locally (model checkpoints will be fetched automatically upon startup)
```shell
pip install -r requirements_demo.txt
streamlit run app.py
```

<p align="center"><img width="600" height="400" alt="Streamlit Demo" src="assets/space_demo.png"></p>

## ✨ Implementation

Our code is written in JAX/ Flax and mainly based upon [jaxnerf](https://github.com/google-research/google-research/tree/master/jaxnerf) from Google Research. The base code is highly optimized in GPU & TPU. For semantic consistency loss, we utilize pretrained CLIP Vision Transformer from [transformers](https://github.com/huggingface/transformers) library.
To learn more about DietNeRF, our experiments and implementation, you are highly recommended to check out our very detailed **[Notion write-up](https://www.notion.so/DietNeRF-Putting-NeRF-on-a-Diet-4aeddae95d054f1d91686f02bdb74745)**!

<p align="center"><img width="500" height="600" alt="스크린샷 2021-07-04 오후 4 11 51" src="assets/report_thumbnail.png"></p> 

##  🤗 Hugging Face Model Hub Repo
You can also find our project on the [Hugging Face Model Hub Repository](https://huggingface.co/flax-community/putting-nerf-on-a-diet/).

Our JAX/Flax implementation currently supports:

<table class="tg">
<thead>
  <tr>
    <th class="tg-0lax"><span style="font-weight:bold">Platform</span></th>
    <th class="tg-0lax" colspan="2"><span style="font-weight:bold">Single-Host GPU</span></th>
    <th class="tg-0lax" colspan="2"><span style="font-weight:bold">Multi-Device TPU</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax"><span style="font-weight:bold">Type</span></td>
    <td class="tg-0lax">Single-Device</td>
    <td class="tg-0lax">Multi-Device</td>
    <td class="tg-0lax">Single-Host</td>
    <td class="tg-0lax">Multi-Host</td>
  </tr>
  <tr>
    <td class="tg-0lax"><span style="font-weight:bold">Training</span></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
  </tr>
  <tr>
    <td class="tg-0lax"><span style="font-weight:bold">Evaluation</span></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
    <td class="tg-0lax"><img src="http://storage.googleapis.com/gresearch/jaxnerf/check.png" alt="Supported" width=18px height=18px></td>
  </tr>
</tbody>
</table>

## 💻 Installation

```bash
# Clone the repo
git clone https://github.com/codestella/putting-nerf-on-a-diet
# Create a conda environment, note you can use python 3.6-3.8 as
# one of the dependencies (TensorFlow) hasn't supported python 3.9 yet.
conda create --name jaxnerf python=3.6.12; conda activate jaxnerf
# Prepare pip
conda install pip; pip install --upgrade pip
# Install requirements
pip install -r requirements.txt
# [Optional] Install GPU and TPU support for Jax
# Remember to change cuda101 to your CUDA version, e.g. cuda110 for CUDA 11.0.
!pip install --upgrade jax "jax[cuda110]" -f https://storage.googleapis.com/jax-releases/jax_releases.html
# install flax and flax-transformer
pip install flax transformers[flax]
```

## ⚽ Dataset 
Download the datasets from the [NeRF official Google Drive](https://drive.google.com/drive/folders/128yBriW1IG_3NJ5Rp7APSTZsJqdJdfc1).
Please download the `nerf_synthetic.zip` and unzip them
in the place you like. Let's assume they are placed under `/tmp/jaxnerf/data/`.


## 💖 Methods

* 👉👉 You can check VEEEERY detailed explanation about our project on [Notion Report](https://www.notion.so/DietNeRF-Putting-NeRF-on-a-Diet-4aeddae95d054f1d91686f02bdb74745)

<p align="center"><img width="400" alt="스크린샷 2021-07-04 오후 4 11 51" src="https://user-images.githubusercontent.com/77657524/124376591-b312b780-dce2-11eb-80ad-9129d6f5eedb.png"></p> 

Based on the principle
that “a bulldozer is a bulldozer from any perspective”, Our proposed DietNeRF supervises the radiance field from arbitrary poses
(DietNeRF cameras). This is possible because we compute a semantic consistency loss in a feature space capturing high-level
scene attributes, not in pixel space. We extract semantic representations of renderings using the CLIP Vision Transformer, then
maximize similarity with representations of ground-truth views. In
effect, we use prior knowledge about scene semantics learned by
single-view 2D image encoders to constrain a 3D representation.

You can check detail information on the author's paper. Also, you can check the CLIP based semantic loss structure on the following image.
<p align="center"><img width="600" alt="스크린샷 2021-07-04 오후 4 11 51" src="https://user-images.githubusercontent.com/77657524/126386709-a4ce7ff8-2a68-442f-b4ed-26971fb90e51.png"></p>

Our code used JAX/FLAX framework for implementation. So that it can achieve much speed up than other NeRF codes. At last, our code used hugging face, transformer,  CLIP model library. 

## 🤟 How to use
```
python -m train \
  --data_dir=/PATH/TO/YOUR/SCENE/DATA \ % e.g., nerf_synthetic/lego
  --train_dir=/PATH/TO/THE/PLACE/YOU/WANT/TO/SAVE/CHECKPOINTS \
  --config=configs/CONFIG_YOU_LIKE
```
You can toggle the semantic loss by “use_semantic_loss” in configuration files.

## 💎 Experimental Results

### ❗ Rendered Rendering images by 8-shot learned Diet-NeRF

DietNeRF has a strong capacity to generalise on novel and challenging views with EXTREMELY SMALL TRAINING SAMPLES!

### HOTDOG / DRUM / SHIP / CHAIR / LEGO / MIC

<img alt="" src="https://user-images.githubusercontent.com/77657524/126976706-caec6d6c-6126-45d0-8680-4c883f71f5bb.png" width="250"/></td><td><img alt="" src="https://user-images.githubusercontent.com/77657524/126976868-183af09a-47b3-4c76-ba20-90e9fef17bcc.png" width="250"/><td><img alt="" src="https://user-images.githubusercontent.com/77657524/126977843-18b4b077-1db0-4287-8e5c-baa10c46e647.png" width="250"/>
<img alt="" src="https://user-images.githubusercontent.com/77657524/126977066-9c99a882-7a46-4a1d-921f-cdb0eee60f39.gif" width="250"/><img alt="" src="https://user-images.githubusercontent.com/77657524/126913553-19ebd2f2-c5f1-4332-a253-950e41cb5229.gif" width="300"/><img alt="" src="https://user-images.githubusercontent.com/77657524/126913559-dfce4b88-84a8-4a0a-91eb-ed12716ab328.gif" width="300"/>

### ❗ Rendered GIF by occluded 14-shot learned NeRF and Diet-NeRF

We made artificial occlusion on the right side of image (Only picked left side training poses).
The reconstruction quality can be compared with this experiment.
DietNeRF shows better quality than Original NeRF when It is occluded.

#### Training poses
<img width="1400" src="https://user-images.githubusercontent.com/26036843/126111980-4f332c87-a7f0-42e0-a355-8e77621bbca4.png">


#### LEGO
[DietNeRF]
<img alt="" src="https://user-images.githubusercontent.com/77657524/126913404-800777f8-8f88-451a-92de-3dda25075206.gif" width="300"/>
[NeRF]
<img alt="" src="https://user-images.githubusercontent.com/77657524/126913412-f10dfb3e-e918-4ff4-aa2c-63529fec91d8.gif" width="300"/>


#### SHIP
[DietNeRF]
<img alt="" src="https://user-images.githubusercontent.com/77657524/126913430-0014a904-6ca1-4a7b-9cd6-6f73b36552fb.gif" width="300"/>
[NeRF]
<img alt="" src="https://user-images.githubusercontent.com/77657524/126913439-2e3128ef-c7ef-4c21-8261-6e3b8fe51f86.gif" width="300"/>


## 👨‍👧‍👦 Our Teams


| Teams            | Members                                                                                                                                                        |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Project Managing | [Stella Yang](https://github.com/codestella) To Watch Our Project Progress, Please Check [Our Project Notion](https://www.notion.so/Putting-NeRF-on-a-Diet-e0caecea0c2b40c3996c83205baf870d) |
| NeRF Team        | [Stella Yang](https://github.com/codestella), [Alex Lau](https://github.com/riven314), [Seunghyun Lee](https://github.com/sseung0703), [Hyunkyu Kim](https://github.com/minus31),  [Haswanth Aekula](https://github.com/hassiahk), [JaeYoung Chung](https://github.com/robot0321)          |
| CLIP Team        | [Seunghyun Lee](https://github.com/sseung0703), [Sasikanth Kotti](https://github.com/ksasi), [Khali Sifullah](https://github.com/khalidsaifullaah) , [Sunghyun Kim](https://github.com/MrBananaHuman)                                |
| Cloud TPU Team   | [Alex Lau](https://github.com/riven314), [Aswin Pyakurel](https://github.com/masapasa), [JaeYoung Chung](https://github.com/robot0321),  [Sunghyun Kim](https://github.com/MrBananaHuman)                                                    |

* Extremely Don't Sleep Contributors 🤣:  [Seunghyun Lee](https://github.com/sseung0703), [Alex Lau](https://github.com/riven314), [Stella Yang](https://github.com/codestella), [Haswanth Aekula](https://github.com/hassiahk)

## 😎 What we improved from original JAX-NeRF : Innovation
 - Neural rendering with fewshot images
 - Hugging face CLIP based semantic loss loop
 - You can choose coarse mlp / coarse + fine mlp training
   (coarse + fine is on the `main` branch / coarse is on the `coarse_only` branch)
    * coarse + fine : shows good geometric reconstruction
    * coarse : shows good PSNR/SSIM result  
 - Make Video/GIF rendering result, `--generate_gif_only` arg can run fast rendering GIF.
 - Cleaning / refactoring the code 
 - Made multiple models / colab / space for Nice demo

## 💞 Social Impact

 - Game Industry
 - Augmented Reality Industry
 - Virtual Reality Industry
 - Graphics Industry
 - Online shopping
 - Metaverse
 - Digital Twin
 - Mapping / SLAM

## 🌱 References
This project is based on “JAX-NeRF”.
```
@software{jaxnerf2020github,
  author = {Boyang Deng and Jonathan T. Barron and Pratul P. Srinivasan},
  title = {{JaxNeRF}: an efficient {JAX} implementation of {NeRF}},
  url = {https://github.com/google-research/google-research/tree/master/jaxnerf},
  version = {0.0},
  year = {2020},
}
```

This project is based on “Putting NeRF on a Diet”.
```
@misc{jain2021putting,
      title={Putting NeRF on a Diet: Semantically Consistent Few-Shot View Synthesis}, 
      author={Ajay Jain and Matthew Tancik and Pieter Abbeel},
      year={2021},
      eprint={2104.00677},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

## 🔑 License
[Apache License 2.0](https://github.com/codestella/putting-nerf-on-a-diet/blob/main/LICENSE)

## ❤️ Special Thanks 

Our Project is started in the [HuggingFace X GoogleAI (JAX) Community Week Event](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104).

Thank you for our mentor Suraj and organizers in JAX/Flax Community Week! 
Our team grows up with this community learning experience. It was wonderful time!

<img width="250" alt="스크린샷 2021-07-04 오후 4 11 51" src="https://user-images.githubusercontent.com/77657524/126369170-5664076c-ac99-4157-bc53-b91dfb7ed7e1.jpeg">

[Common Computer AI](https://comcom.ai/en/) sponsored multiple V100 GPUs for our project!
Thank you so much for your support!
<img width="250" alt="스크린샷" src="https://user-images.githubusercontent.com/77657524/126914984-d959be06-19f4-4228-8d3a-a855396b2c3f.jpeg">



