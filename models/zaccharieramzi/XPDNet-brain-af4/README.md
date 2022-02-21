# XPDNet-brain-af4
---
tags:
- TensorFlow
- MRI reconstruction
- MRI
datasets:
- fastMRI
---

This model was used to achieve the 3rd highest submission in terms of PSNR on the fastMRI dataset (see https://fastmri.org/leaderboards/).
It is a base model for acceleration factor 4.
The model uses 25 iterations and a medium MWCNN, and a big sensitivity maps refiner.

## Model description
For more details, see https://arxiv.org/abs/2010.07290.
This section is WIP.

## Intended uses and limitations
This model can be used to reconstruct brain data from Siemens scanner at acceleration factor 4.
It was shown [here](https://arxiv.org/abs/2106.00753), that it can generalize well, although further tests are required.

## How to use
This model can be loaded using the following repo: https://github.com/zaccharieramzi/fastmri-reproducible-benchmark.
After cloning the repo, `git clone https://github.com/zaccharieramzi/fastmri-reproducible-benchmark`, you can install the package via `pip install fastmri-reproducible-benchmark`.
The framework is TensorFlow.

You can initialize and load the model weights as follows:
```python
import tensorflow as tf

from fastmri_recon.models.subclassed_models.denoisers.proposed_params import get_model_specs
from fastmri_recon.models.subclassed_models.xpdnet import XPDNet


n_primal = 5
model_fun, model_kwargs, n_scales, res = [
        (model_fun, kwargs, n_scales, res)
        for m_name, m_size, model_fun, kwargs, _, n_scales, res in get_model_specs(n_primal=n_primal, force_res=False)
        if m_name == 'MWCNN' and m_size == 'medium'
][0]
model_kwargs['use_bias'] = False
run_params = dict(
    n_primal=n_primal,
    multicoil=True,
    n_scales=n_scales,
    refine_smaps=True,
    refine_big=True,
    res=res,
    output_shape_spec=True,
    n_iter=25,
)
model = XPDNet(model_fun, model_kwargs, **run_params)
kspace_size = [1, 1, 320, 320]
inputs = [
    tf.zeros(kspace_size + [1], dtype=tf.complex64),  # kspace
    tf.zeros(kspace_size, dtype=tf.complex64),  # mask
    tf.zeros(kspace_size, dtype=tf.complex64),  # smaps
    tf.constant([[320, 320]]),  # shape
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
    shape,  # shape: [n_slices, 2]
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
On the fastMRI validation dataset, the same model with a smaller sensitivity maps refiner gives the following results for 30 validation volumes per contrast:

| Contrast | T1     | T2     | FLAIR  | T1-POST |
|----------|--------|--------|--------|---------|
| PSNR     | 41.56  | 40.68  | 39.60  | 42.53   |
| SSIM     | 0.9506 | 0.9554 | 0.9321 | 0.9683  |

Further results can be seen on the fastMRI leaderboards for the test and challenge dataset: https://fastmri.org/leaderboards/


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

