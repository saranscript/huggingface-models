---
language: hi
tags:
- roberta
license: cc-by-4.0
datasets:
- HASOC 2021
widget:
- text: "I like you. </s></s> I love you."
---


## hate-roberta-hasoc-hindi

hate-roberta-hasoc-hindi is a binary hate speech model fine-tuned on Hindi Hasoc Hate Speech Dataset 2021.
The label mappings are 0 -> None, 1 -> Hate.

More details on the dataset, models, and baseline results can be found in our [paper] (https://arxiv.org/abs/2110.12200)

```
@article{velankar2021hate,
  title={Hate and Offensive Speech Detection in Hindi and Marathi},
  author={Velankar, Abhishek and Patil, Hrushikesh and Gore, Amol and Salunke, Shubham and Joshi, Raviraj},
  journal={arXiv preprint arXiv:2110.12200},
  year={2021}
}
```