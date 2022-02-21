# NCPDNet-multicoil-radial
---
tags:
- TensorFlow
- MRI reconstruction
- MRI
datasets:
- fastMRI
---

This is a non-Cartesian multicoil MRI reconstruction model for radial trajectories at acceleration factor 4.
The model uses 10 iterations and a small vanilla CNN.

## Model description
For more details, see https://hal.inria.fr/hal-03188997.
This section is WIP.

## Intended uses and limitations
This model can be used to reconstruct multicoil knee data from Siemens scanner at acceleration factor 4 in a radial acquisition setting.

## How to use
This model can be loaded using the following repo: https://github.com/zaccharieramzi/fastmri-reproducible-benchmark.
After cloning the repo, `git clone https://github.com/zaccharieramzi/fastmri-reproducible-benchmark`, you can install the package via `pip install fastmri-reproducible-benchmark`.
The framework is TensorFlow.

You can initialize and load the model weights as follows:
```python
import tensorflow as tf

from fastmri_recon.models.subclassed_models.ncpdnet import NCPDNet


model = NCPDNet(
    multicoil=True,
    im_size=(640, 400),
    dcomp=True,
    refine_smaps=True,
)
kspace_shape = 1
inputs = [
    tf.zeros([1, 1, kspace_shape, 1], dtype=tf.complex64),
    tf.zeros([1, 2, kspace_shape], dtype=tf.float32),
    tf.zeros([1, 1, 640, 320], dtype=tf.complex64),
    (tf.constant([320]), tf.ones([1, kspace_shape], dtype=tf.float32)),
]
model(inputs)
model.load_weights('model_weights.h5')
```

Using the model is then as simple as:
```python
model([
    kspace,  # shape: [n_slices, n_coils, n_kspace_samples, 1]
    traj,  # shape: [n_slices, n_coils, 2, n_kspace_samples]
    smaps,  # shape: [n_slices, n_coils, n_kspace_samples, n_coils]
    (
        output_shape,  # shape: [n_slices, 1]
        dcomp,  # shape: [n_slices, n_kspace_samples]
    )
])
```

## Limitations and bias
The limitations and bias of this model have not been properly investigated.

## Training data
This model was trained using the [fastMRI dataset](https://fastmri.org/dataset/).

## Training procedure
The training procedure is described in https://hal.inria.fr/hal-03188997.
This section is WIP.

## Evaluation results
On the fastMRI validation dataset:
- PSNR: 40.00
- SSIM: 0.9191


## Bibtex entry
```
@unpublished{ramzi:hal-03188997,
  TITLE = {{NC-PDNet: a Density-Compensated Unrolled Network for 2D and 3D non-Cartesian MRI Reconstruction}},
  AUTHOR = {Ramzi, Zaccharie and G R, Chaithya and Starck, Jean-Luc and Ciuciu, Philippe},
  YEAR = {2021},
  MONTH = Sep,
}
```

