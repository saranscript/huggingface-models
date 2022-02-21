# UNet-OASIS
---
tags:
- TensorFlow
- MRI reconstruction
- MRI
datasets:
- OASIS
---

This model can be used to reconstruct single coil OASIS data with an acceleration factor of 4.

## Model description
For more details, see https://www.mdpi.com/2076-3417/10/5/1816.
This section is WIP.

## Intended uses and limitations
This model can be used to reconstruct single coil brain retrospective data from the OASIS database at acceleration factor 4.
It cannot be used on multi-coil data.

## How to use
This model can be loaded using the following repo: https://github.com/zaccharieramzi/fastmri-reproducible-benchmark.
After cloning the repo, `git clone https://github.com/zaccharieramzi/fastmri-reproducible-benchmark`, you can install the package via `pip install fastmri-reproducible-benchmark`.
The framework is TensorFlow.

You can initialize and load the model weights as follows:
```python
from fastmri_recon.models.functional_models.unet import unet


model = unet(n_layers=4, layers_n_channels=[16, 32, 64, 128], layers_n_non_lins=2,)
model.load_weights('UNet-fastmri/model_weights.h5')

```

Using the model is then as simple as:
```python
model(zero_filled_recon)
```

## Limitations and bias
The limitations and bias of this model have not been properly investigated.

## Training data
This model was trained using the [OASIS dataset](https://www.oasis-brains.org/).

## Training procedure
The training procedure is described in https://www.mdpi.com/2076-3417/10/5/1816 for brain data.
This section is WIP.

## Evaluation results
This model was evaluated using the [OASIS dataset](https://www.oasis-brains.org/).

- PSNR: 29.8
- SSIM: 0.847


## Bibtex entry
```
@article{ramzi2020benchmarking,
  title={Benchmarking MRI reconstruction neural networks on large public datasets},
  author={Ramzi, Zaccharie and Ciuciu, Philippe and Starck, Jean-Luc},
  journal={Applied Sciences},
  volume={10},
  number={5},
  pages={1816},
  year={2020},
  publisher={Multidisciplinary Digital Publishing Institute}
}
```

