---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- accuracy
model-index:
- name: xtremedistil-l6-h384-emotion
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: emotion
      type: emotion
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.928
---
# xtremedistil-l6-h384-emotion
This model is a fine-tuned version of [microsoft/xtremedistil-l6-h384-uncased](https://huggingface.co/microsoft/xtremedistil-l6-h384-uncased) on the emotion dataset.
It achieves the following results on the evaluation set:
- Accuracy: 0.928

This model can be quantized to int8 and retain accuracy 
- Accuracy 0.912

<pre>
import transformers
import transformers.convert_graph_to_onnx as onnx_convert
from pathlib import Path

pipeline = transformers.pipeline("text-classification",model=model,tokenizer=tokenizer)
onnx_convert.convert_pytorch(pipeline, opset=11, output=Path("xtremedistil-l6-h384-emotion.onnx"), use_external_format=False)
from onnxruntime.quantization import quantize_dynamic, QuantType
quantize_dynamic("xtremedistil-l6-h384-emotion.onnx", "xtremedistil-l6-h384-emotion-int8.onnx", 
                 weight_type=QuantType.QUInt8)
</pre>


### Training hyperparameters
The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 128
- eval_batch_size: 8
- seed: 42
- num_epochs: 14
### Training results
<pre>
Epoch	Training Loss	Validation Loss	Accuracy
1	No log	0.960511	0.689000
2	No log	0.620671	0.824000
3	No log	0.435741	0.880000
4	0.797900	0.341771	0.896000
5	0.797900	0.294780	0.916000
6	0.797900	0.250572	0.918000
7	0.797900	0.232976	0.924000
8	0.277300	0.216347	0.924000
9	0.277300	0.202306	0.930500
10	0.277300	0.192530	0.930000
11	0.277300	0.192500	0.926500
12	0.181700	0.187347	0.928500
13	0.181700	0.185896	0.929500
14	0.181700	0.185154	0.928000
</pre>