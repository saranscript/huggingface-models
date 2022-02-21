# UPDNet-knee-af4
---
tags:
- TensorFlow
- MRI reconstruction
- MRI
datasets:
- fastMRI
---

This model was used to achieve the 9th highest submission in terms of PSNR on the fastMRI dataset (see https://fastmri.org/leaderboards/) (0.2dB behind the 2nd submission).
It is a base model for acceleration factor 4.
The model uses 25 iterations and a medium-ca-prelu U-net, and a medium sensitivity maps refiner.

## Model description
For more details, see https://arxiv.org/abs/2010.07290.
This section is WIP.

## Intended uses and limitations
This model can be used to reconstruct knee data from Siemens scanner at acceleration factor 4.

## How to use
This model can be loaded using the following repo: https://github.com/zaccharieramzi/fastmri-reproducible-benchmark.
After cloning the repo, `git clone https://github.com/zaccharieramzi/fastmri-reproducible-benchmark`, you can install the package via `pip install fastmri-reproducible-benchmark`.
The framework is TensorFlow.

You can initialize and load the model weights as follows:
```python
import tensorflow as tf

from fastmri_recon.models.subclassed_models.updnet import UPDNet


model = UPDNet(
    multicoil=True,
    n_dual=1,
    primal_only=True,
    n_layers=4,
    n_iter=25,
    channel_attention_kwargs={'dense': True},
    refine_smaps=True,
    non_linearity='prelu',
    layers_n_channels=[16 * 2**i for i in range(4)],
)
kspace_size = [1, 1, 320, 320]
inputs = [
    tf.zeros(kspace_size + [1], dtype=tf.complex64),  # kspace
    tf.zeros(kspace_size, dtype=tf.complex64),  # mask
    tf.zeros(kspace_size, dtype=tf.complex64),  # smaps
]
model(inputs)
model.load_weights('model_weights.h5')
```

Using the model is then as simple as:
```python
model([
    kspace,  # shape: [n_slices, n_coils, n_rows, n_cols, 1]
    mask,  # shape: [n_slices, n_coils, n_rows, n_cols]
    smaps,  # shape: [n_slices, n_coils, n_rows, n_cols]
])
```

## Limitations and bias
The limitations and bias of this model have not been properly investigated.

## Training data
This model was trained using the [fastMRI dataset](https://fastmri.org/dataset/).

## Training procedure
The training procedure is described in https://arxiv.org/abs/2010.07290.
This section is WIP.

## Evaluation results
No evaluation available outside the one from the fastMRI leaderboard (id: `updnet_v3`).


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

