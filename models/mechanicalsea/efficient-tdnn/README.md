---
language:
- en
license: mit
tags:
- embeddings
- Speaker
- Verification
- Identification
- NAS
- TDNN
- pytorch
datasets:
- voxceleb1
- voxceleb2
metrics:
- EER
- minDCF:
  - p_target: 0.01
---


# EfficientTDNN

This repository provides all the necessary tools to perform speaker verification with a NAS alternative, named as EfficientTDNN.
The system can be used to extract speaker embeddings with different model size.
It is trained on Voxceleb2 training data using data augmentation.
The model performance on Voxceleb1-test set(Cleaned)/Vox1-O are reported as follows.

| Supernet Stage | Subnet | MACs (3s) | Params | EER(%) | minDCF |
|:-------------:|:--------------:|:--------------:|:--------------:|:--------------:|:--------------:|
| depth | Base | 1.45G | 5.79M | 0.94 | 0.089 |
| width 1 | Mobile | 570.98M | 2.42M | 1.41 | 0.124 |
| width 2 | Small | 204.07M | 899.20K | 2.20 | 0.219 |

The details of three subnets are:

- Base: (3, [512, 512, 512, 512], [5, 3, 3, 3], 1536)
- Mobile: (3, [384, 256, 256, 256], [5, 3, 3, 3], 768)
- Small: (2, [256, 256, 256], [3, 3, 3], 400)

## Compute your speaker embeddings

```python
import torchaudio
from sugar.models import WrappedModel
wav_file = f"{vox1_root}/id10270/x6uYqmx31kE/00001.wav"
signal, fs =torchaudio.load(wav_file)

repo_id = "mechanicalsea/efficient-tdnn"
supernet_filename = "depth/depth.torchparams"
subnet_filename = "depth/depth.ecapa-tdnn.3.512.512.512.512.5.3.3.3.1536.bn.tar"
subnet, info = WrappedModel.from_pretrained(
    repo_id=repo_id, supernet_filename=supernet_filename, subnet_filename=subnet_filename)

embedding = subnet(signal)
```

## Inference on GPU

To perform inference on the GPU, add  `subnet = subnet.to(device)`  after calling the `from_pretrained` method.

## Model Description

Models are listed as follows.

- **Dynamic Kernel**: The model enables various kernel sizes in {1,3,5}, `kernel/kernel.torchparams`.
- **Dynamic Depth**: The model enables additional various depth in {2,3,4} based on **Dynamic Kernel** version, `depth/depth.torchparams`.
- **Dynamic Width 1**: The model enable additional various width in [0.5, 1.0] based on **Dynamic Depth** version, `width1/width1.torchparams`.
- **Dynamic Width 2**: The model enable additional various width in [0.25, 0.5] based on **Dynamic Width 1** version, `width2/width2.torchparams`.

Furthermore, some subnets are given in the form of the weights of batchnorm corresponding to their trained supernets as follows.

- **Dynamic Kernel**
  1. `kernel/kernel.max.bn.tar`
  2. `kernel/kernel.Kmin.bn.tar`
- **Dynamic Depth**
  1. `depth/depth.max.bn.tar`
  2. `depth/depth.Kmin.bn.tar`
  3. `depth/depth.Dmin.bn.tar`
  4. `depth/depth.3.512.5.5.3.3.1536.bn.tar`
  5. `depth/depth.ecapa-tdnn.3.512.512.512.512.5.3.3.3.1536.bn.tar`
- **Dynamic Width 1**
  1. `width1/width1.torchparams`
  2. `width1/width1.max.bn.tar`
  3. `width1/width1.Kmin.bn.tar`
  4. `width1/width1.Dmin.bn.tar`
  5. `width1/width1.C1min.bn.tar`
  6. `width1/width1.3.383.256.256.256.5.3.3.3.768.bn.tar`
- **Dynamic Width 2**
  1. `width2/width2.max.bn.tar`
  2. `width2/width2.Kmin.bn.tar`
  3. `width2/width2.Dmin.bn.tar`
  4. `width2/width2.C1min.bn.tar`
  5. `width2/width2.C2min.bn.tar`
  6. `width2/width2.3.384.3.1152.bn.tar`
  7. `width2/width2.3.256.256.384.384.1.3.5.3.1152.bn.tar`
  8. `width2/width2.2.256.256.256.3.3.3.400.bn.tar`

The tag is described as follows.

- max: (4, [512, 512, 512, 512, 512], [5, 5, 5, 5, 5], 1536)
- Kmin: (4, [512, 512, 512, 512, 512], [1, 1, 1, 1, 1], 1536)
- Dmin: (2, [512, 512, 512], [1, 1, 1], 1536)
- C1min: (2, [256, 256, 256], [1, 1, 1], 768)
- C2min: (2, [128, 128, 128], [1, 1, 1], 384)

More details about EfficentTDNN can be found in the paper [EfficientTDNN](https://arxiv.org/abs/2103.13581).

## **Citing EfficientTDNN**

Please, cite EfficientTDNN if you use it for your research or business.

```bibtex
@article{rwang-efficienttdnn-2021,
  title={{EfficientTDNN}: Efficient Architecture Search for Speaker Recognition},
  author={Rui Wang and Zhihua Wei and Haoran Duan and Shouling Ji and Yang Long and Zhen Hong},
  journal={arXiv preprint arXiv:2103.13581},
  year={2021},
  eprint={2103.13581},
  archivePrefix={arXiv},
  primaryClass={eess.AS},
  note={arXiv:2103.13581}
}
```
