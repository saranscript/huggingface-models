## Lawformer

### Introduction
This repository provides the source code and checkpoints of the paper "Lawformer: A Pre-trained Language Model forChinese Legal Long Documents". You can download the checkpoint from the [huggingface model hub](https://huggingface.co/xcjthu/Lawformer) or from [here](https://data.thunlp.org/legal/Lawformer.zip).



### Easy Start
We have uploaded our model to the huggingface model hub. Make sure you have installed transformers.
```python
>>> from transformers import AutoModel, AutoTokenizer
>>> tokenizer = AutoTokenizer.from_pretrained("hfl/chinese-roberta-wwm-ext")
>>> model = AutoModel.from_pretrained("xcjthu/Lawformer")
>>> inputs = tokenizer("任某提起诉讼，请求判令解除婚姻关系并对夫妻共同财产进行分割。", return_tensors="pt")
>>> outputs = model(**inputs)
```

### Cite
If you use the pre-trained models, please cite this paper:
```
@article{xiao2021lawformer,
  title={Lawformer: A Pre-trained Language Model forChinese Legal Long Documents},
  author={Xiao, Chaojun and Hu, Xueyu and Liu, Zhiyuan and Tu, Cunchao and Sun, Maosong},
  year={2021}
}
```

