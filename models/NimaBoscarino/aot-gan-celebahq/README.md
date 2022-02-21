---
tags:
- face-recognition
- face-generation
- face-segmentation
- generative-adversarial-network
metrics:
- L1
- PSNR
- SSIM
- FID
datasets:
- celeba-hq
---
# AOT-GAN CelebA-HQ
AOT-GAN is a model that can be used for image in-painting. The CelebA-HQ checkpoint is trained on synthetic human faces, which should make it suitable for touching up and restoring portraits.

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
The CelebA-HQ dataset was created with this codebase: https://github.com/tkarras/progressive_growing_of_gans, owned by NVidia and licensed under Creative Commons Attribution-NonCommercial 4.0 International.