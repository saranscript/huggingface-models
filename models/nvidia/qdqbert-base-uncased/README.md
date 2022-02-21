<!---
Copyright 2021 NVIDIA Corporation. All rights reserved.
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# QDQBERT base model (uncased)

## Model description
[QDQBERT](https://huggingface.co/docs/transformers/model_doc/qdqbert) model inserts fake quantization operations (pair of QuantizeLinear/DequantizeLinear operators) to (i) linear layer inputs and weights, (ii) matmul inputs, (iii) residual add inputs, in BERT model.

QDQBERT model can be loaded from any checkpoint of HuggingFace BERT model (for example bert-base-uncased), and perform Quantization Aware Training/Post Training Quantization.

In this model card, **qdqbert-base-uncased** corresponds to the **bert-base-uncased** model with QuantizeLinear/DequantizeLinear ops (**Q/DQ nodes**). Similarly, one can also use the QDQBERT model for qdqbert-large-cased corresponding to bert-large-cased, etc.

## How to run QDQBERT using Transformers

### Prerequisites
QDQBERT requires the dependency of [Pytorch Quantization Toolkit](https://github.com/NVIDIA/TensorRT/tree/main/tools/pytorch-quantization). To install Pytorch Quantization Toolkit, run
```
pip install pytorch-quantization --extra-index-url https://pypi.ngc.nvidia.com
```

### Set default quantizers
QDQBERT model inserts Q/DQ nodes to BERT by **TensorQuantizer** in Pytorch Quantization Toolkit. **TensorQuantizer** is the module for quantizing tensors, with **QuantDescriptor** defining how the tensor should be quantized. Refer to [Pytorch Quantization Toolkit userguide](https://docs.nvidia.com/deeplearning/tensorrt/pytorch-quantization-toolkit/docs/userguide.html) for more details.

Before creating QDQBERT model, one has to set the default **QuantDescriptor** defining default tensor quantizers. Example:

```python
import pytorch_quantization.nn as quant_nn
from pytorch_quantization.tensor_quant import QuantDescriptor
# The default tensor quantizer is set to use Max calibration method
input_desc = QuantDescriptor(num_bits=8, calib_method="max")
# The default tensor quantizer is set to be per-channel quantization for weights
weight_desc = QuantDescriptor(num_bits=8, axis=((0,)))
quant_nn.QuantLinear.set_default_quant_desc_input(input_desc)
quant_nn.QuantLinear.set_default_quant_desc_weight(weight_desc)
```

### Calibration
Calibration is the terminology of passing data samples to the quantizer and deciding the best scaling factors for tensors. After setting up the tensor quantizers, one can use the following example to calibrate the model:

```python
# Find the TensorQuantizer and enable calibration
for name, module in model.named_modules():
    if name.endswith('_input_quantizer'):
        module.enable_calib()
        module.disable_quant()  # Use full precision data to calibrate
# Feeding data samples
model(x)
# ...
# Finalize calibration
for name, module in model.named_modules():
    if name.endswith('_input_quantizer'):
        module.load_calib_amax()
        module.enable_quant()
# If running on GPU, it needs to call .cuda() again because new tensors will be created by calibration process
model.cuda()
# Keep running the quantized model
# ...
```

### Export to ONNX
The goal of exporting to ONNX is to deploy inference by [TensorRT](https://developer.nvidia.com/tensorrt). Fake quantization will be broken into a pair of QuantizeLinear/DequantizeLinear ONNX ops. After setting the static member **TensorQuantizer** to use Pytorch’s own fake quantization functions, fake quantized model can be exported to ONNX, follow the instructions in [torch.onnx](https://pytorch.org/docs/stable/onnx.html). Example:

```python
from pytorch_quantization.nn import TensorQuantizer
TensorQuantizer.use_fb_fake_quant = True
# Load the calibrated model
...
# ONNX export
torch.onnx.export(...)
```

## Complete example
A complete example of using QDQBERT model to perform Quatization Aware Training and Post Training Quantization for SQUAD task can be found at [transformers/examples/research_projects/quantization-qdqbert](https://github.com/huggingface/transformers/tree/master/examples/research_projects/quantization-qdqbert)