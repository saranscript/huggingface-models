---
language: zh
tags:
- roberta-wwm
license: apache-2.0
datasets:
- finance
---

在众多业务中，越来越频繁的使用预训练语言模型（Pre-trained Language Models），为了在金融场景下各任务中取得更好效果，我们发布了jdt-fin-roberta-wwm模型

#### 模型&下载
* `base模型`：12-layer, 768-hidden, 12-heads, 110M parameters  

| 模型简称 | 京盘下载 |
| :----: | :----:|
| fin-roberta-wwm | [Tensorflow](https://3.cn/103c-hwSS)/[Pytorch](https://3.cn/103c-izpe) |
| fin-roberta-wwm-large | todo |

#### 快速加载
依托于[Huggingface-Transformers](https://github.com/huggingface/transformers)，可轻松调用以上模型。
```
tokenizer = BertTokenizer.from_pretrained("MODEL_NAME")
model = BertModel.from_pretrained("MODEL_NAME")
```
**注意：本目录中的所有模型均使用BertTokenizer以及BertModel加载，请勿使用RobertaTokenizer/RobertaModel！**
其中`MODEL_NAME`对应列表如下：

| 模型名 | MODEL_NAME |
| - | - |
| fin-roberta-wwm | wangfan/jdt-fin-roberta-wwm |
| fin-roberta-wwm-large | todo |

#### 任务效果
| Task | NER | 关系抽取 | 事件抽取 | 指标抽取 | 实体链接 | 
|:----:|:-- :|:------:|:-------:|:-------:|:------:|
| Our  |93.88| 79.02 | 91.99 | 94.28| 86.72 |
| Roberta-wwm |93.47| 76.99 | 91.58 | 93.98| 85.20 |

