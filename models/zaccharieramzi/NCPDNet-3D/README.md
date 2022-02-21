# NCPDNet-3D
---
tags:
- TensorFlow
- MRI reconstruction
- MRI
datasets:
- OASIS
---

This is a non-Cartesian 3D MRI reconstruction model for radial trajectories at acceleration factor 4.
The model uses 10 iterations and a small vanilla CNN.

## Model description
For more details, see https://hal.inria.fr/hal-03188997.
This section is WIP.

## Intended uses and limitations
This model can be used to reconstruct 3D brain data obtained retrospectively from magnitude scanners of the OASIS database at acceleration factor 4 in a fully radial acquisition setting.

## How to use
This model can be loaded using the following repo: https://github.com/zaccharieramzi/fastmri-reproducible-benchmark.
After cloning the repo, `git clone https://github.com/zaccharieramzi/fastmri-reproducible-benchmark`, you can install the package via `pip install fastmri-reproducible-benchmark`.
The framework is TensorFlow.

You can initialize and load the model weights as follows:
```python
import tensorflow as tf

from fastmri_recon.models.subclassed_models.ncpdnet import NCPDNet


model = NCPDNet(
    three_d=True,
    n_iter=6,
    n_filters=16,
    im_size=(176, 256, 256),
    dcomp=True,
    fastmri=False,
)
kspace_shape = 1
inputs = [
    tf.zeros([1, 1, kspace_shape, 1], dtype=tf.complex64),
    tf.zeros([1, 3, kspace_shape], dtype=tf.float32),
    (tf.constant([(176, 256, 256)]), tf.ones([1, kspace_shape], dtype=tf.float32)),
]
model(inputs)
model.load_weights('model_weights.h5')
```

Using the model is then as simple as:
```python
model([
    kspace,  # shape: [n_batch, 1, n_kspace_samples, 1]
    traj,  # shape: [n_batch, 1, 3, n_kspace_samples]
    (
        output_shape,  # shape: [n_batch, 3]
        dcomp,  # shape: [n_batch, n_kspace_samples]
    )
])
```

## Limitations and bias
The limitations and bias of this model have not been properly investigated.

## Training data
This model was trained using the [OASIS dataset](https://www.oasis-brains.org/).

## Training procedure
The training procedure is described in https://hal.inria.fr/hal-03188997.
This section is WIP.

## Evaluation results
On the OASIS validation dataset:
- PSNR: 33.76

## Bibtex entry
```
@unpublished{ramzi:hal-03188997,
  TITLE = {{NC-PDNet: a Density-Compensated Unrolled Network for 2D and 3D non-Cartesian MRI Reconstruction}},
  AUTHOR = {Ramzi, Zaccharie and G R, Chaithya and Starck, Jean-Luc and Ciuciu, Philippe},
  YEAR = {2021},
  MONTH = Sep,
}
```

