---
language: en
thumbnail: https://github.com/junnyu
tags:
- pytorch
- electra
license: mit
datasets:
- openwebtext
---
# 一、 个人在openwebtext数据集上训练得到的electra-small模型

# 二、 复现结果(dev dataset)
|Model|CoLA|SST|MRPC|STS|QQP|MNLI|QNLI|RTE|Avg.|
|---|---|---|---|---|---|---|---|---|---|
|Metrics|MCC|Acc|Acc|Spearman|Acc|Acc|Acc|Acc||
|ELECTRA-Small-OWT(original)|56.8|88.3|87.4|86.8|88.3|78.9|87.9|68.5|80.36|
|**ELECTRA-Small-OWT (this)**| 55.82 |89.67|87.0|86.96|89.28|80.08|87.50|66.07|80.30|

# 三、 训练细节
- 数据集 openwebtext
- 训练batch_size 256
- 学习率lr  5e-4
- 最大句子长度max_seqlen  128
- 训练total step  62.5W
- GPU RTX3090
- 训练时间总共耗费2.5天

# 四、 使用
```python
import torch
from transformers.models.electra import ElectraModel, ElectraTokenizer
tokenizer = ElectraTokenizer.from_pretrained("junnyu/electra_small_discriminator")
model = ElectraModel.from_pretrained("junnyu/electra_small_discriminator")
inputs = tokenizer("Beijing is the capital of China.", return_tensors="pt")
with torch.no_grad():
    outputs = model(**inputs)
    print(outputs[0].shape)
```