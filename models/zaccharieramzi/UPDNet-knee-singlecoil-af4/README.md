# UPDNet-knee-singlecoil-af4
---
tags:
- TensorFlow
- MRI reconstruction
- MRI
datasets:
- fastMRI
---

This model can be used to reconstruct single coil fastMRI data with an acceleration factor of 4.

## Model description
For more details, see https://arxiv.org/abs/2010.07290.
This section is WIP.

## Intended uses and limitations
This model can be used to reconstruct single coil knee data from Siemens scanner at acceleration factor 4.
It cannot be used on multi-coil data.

## How to use
This model can be loaded using the following repo: https://github.com/zaccharieramzi/fastmri-reproducible-benchmark.
After cloning the repo, `git clone https://github.com/zaccharieramzi/fastmri-reproducible-benchmark`, you can install the package via `pip install fastmri-reproducible-benchmark`.
The framework is TensorFlow.

You can initialize and load the model weights as follows:
```python
import tensorflow as tf

from fastmri_recon.models.subclassed_models.updnet import UPDNet


model = UPDNet(
    n_dual=1,
    primal_only=True,
    layers_n_channels=[16 * 2**i for i in range(3)],
)
kspace_size = [1, 320, 320]
inputs = [
    tf.zeros(kspace_size + [1], dtype=tf.complex64),  # kspace
    tf.zeros(kspace_size, dtype=tf.complex64),  # mask
]
model(inputs)
model.load_weights('model_weights.h5')
```

Using the model is then as simple as:
```python
model([
    kspace,  # shape: [n_slices, n_rows, n_cols, 1]
    mask,  # shape: [n_slices, n_rows, n_cols]
])
```

## Limitations and bias
The limitations and bias of this model have not been properly investigated.

## Training data
This model was trained using the [fastMRI dataset](https://fastmri.org/dataset/).

## Training procedure
The training procedure is described in https://arxiv.org/abs/2010.07290 for brain data.
This section is WIP.

## Evaluation results
Not available


## Bibtex entry
```
@inproceedings{Ramzi2020d,
archivePrefix = {arXiv},
arxivId = {2010.07290},
author = {Ramzi, Zaccharie and Ciuciu, Philippe and Starck, Jean-Luc},
booktitle = {ISMRM},
eprint = {2010.07290},
pages = {1--4},
title = {{XPDNet for MRI Reconstruction: an application to the 2020 fastMRI challenge}},
url = {http://arxiv.org/abs/2010.07290},
year = {2021}
}
```

