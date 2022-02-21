---
tags:
- scene-recognition
- scene-generation
- generative-adversarial-network
metrics:
- L1
- PSNR
- SSIM
- FID
datasets:
- places2
---
# AOT-GAN Places2
AOT-GAN is a model that can be used for image in-painting. The Places2 checkpoint is trained on a dataset which should make it suitable for touching up and restoring images of landscapes, buildings, and other natural and developed places.

This model was generated using [AOT-GAN-for-Inpainting](https://github.com/researchmm/AOT-GAN-for-Inpainting), cited as

```
@inproceedings{yan2021agg,
  author = {Zeng, Yanhong and Fu, Jianlong and Chao, Hongyang and Guo, Baining},
  title = {Aggregated Contextual Transformations for High-Resolution Image Inpainting},
  booktitle = {Arxiv},
  pages={-},
  year = {2020}
}
```

## Dataset
The Places2 dataset can be found here: http://places2.csail.mit.edu/download.html