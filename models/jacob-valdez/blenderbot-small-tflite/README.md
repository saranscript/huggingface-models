---
language: "en"
#thumbnail: "url to a thumbnail used in social sharing"
tags:
- Android
- tflite
- blenderbot
license: "apache-2.0"
#datasets:
#metrics:
---
# Model Card

`blenderbot-small-tflite` is a tflite version of `blenderbot-small-90M` I converted for my UTA CSE3310 class. See the repo at [https://github.com/kmosoti/DesparadosAEYE](https://github.com/kmosoti/DesparadosAEYE) and the conversion process [here](https://drive.google.com/file/d/1F93nMsDIm1TWhn70FcLtcaKQUynHq9wS/view?usp=sharing).

You have to right pad your user and model input integers to make them [32,]-shaped. Then indicate te true length with the 3rd and 4th params.

```python
display(interpreter.get_input_details())
display(interpreter.get_output_details())
```

```json
[{'dtype': numpy.int32,
  'index': 0,
  'name': 'input_tokens',
  'quantization': (0.0, 0),
  'quantization_parameters': {'quantized_dimension': 0,
   'scales': array([], dtype=float32),
   'zero_points': array([], dtype=int32)},
  'shape': array([32], dtype=int32),
  'shape_signature': array([32], dtype=int32),
  'sparsity_parameters': {}},
 {'dtype': numpy.int32,
  'index': 1,
  'name': 'decoder_input_tokens',
  'quantization': (0.0, 0),
  'quantization_parameters': {'quantized_dimension': 0,
   'scales': array([], dtype=float32),
   'zero_points': array([], dtype=int32)},
  'shape': array([32], dtype=int32),
  'shape_signature': array([32], dtype=int32),
  'sparsity_parameters': {}},
 {'dtype': numpy.int32,
  'index': 2,
  'name': 'input_len',
  'quantization': (0.0, 0),
  'quantization_parameters': {'quantized_dimension': 0,
   'scales': array([], dtype=float32),
   'zero_points': array([], dtype=int32)},
  'shape': array([], dtype=int32),
  'shape_signature': array([], dtype=int32),
  'sparsity_parameters': {}},
 {'dtype': numpy.int32,
  'index': 3,
  'name': 'decoder_input_len',
  'quantization': (0.0, 0),
  'quantization_parameters': {'quantized_dimension': 0,
   'scales': array([], dtype=float32),
   'zero_points': array([], dtype=int32)},
  'shape': array([], dtype=int32),
  'shape_signature': array([], dtype=int32),
  'sparsity_parameters': {}}]
[{'dtype': numpy.int32,
  'index': 3113,
  'name': 'Identity',
  'quantization': (0.0, 0),
  'quantization_parameters': {'quantized_dimension': 0,
   'scales': array([], dtype=float32),
   'zero_points': array([], dtype=int32)},
  'shape': array([1], dtype=int32),
  'shape_signature': array([1], dtype=int32),
  'sparsity_parameters': {}}]
```