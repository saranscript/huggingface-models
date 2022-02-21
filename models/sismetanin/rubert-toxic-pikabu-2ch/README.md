---
language: 
- ru

tags:
- toxic comments classification
---

## RuBERT-Toxic
RuBERT-Toxic is a [RuBERT](https://huggingface.co/DeepPavlov/rubert-base-cased) model fine-tuned on [Kaggle Russian Language Toxic Comments Dataset](https://www.kaggle.com/blackmoon/russian-language-toxic-comments). You can find a detailed description of the data used and the fine-tuning process in [this article](http://doi.org/10.28995/2075-7182-2020-19-1149-1159). You can also find this information at [GitHub](https://github.com/sismetanin/toxic-comments-detection-in-russian).

| System  | P | R | F<sub>1</sub> | 
| ------------- | ------------- | ------------- | ------------- | 
| MNB-Toxic | 87.01% | 81.22% | 83.21% |
| M-BERT<sub>Base</sub>-Toxic | 91.19% | 91.10% | 91.15% |
| <b>RuBERT-Toxic</b> | <b>91.91%</b> | <b>92.51%</b> | <b>92.20%</b> |
| M-USE<sub>CNN</sub>-Toxic | 89.69% | 90.14% | 89.91% |
| M-USE<sub>Trans</sub>-Toxic | 90.85% | 91.92% | 91.35% |

We fine-tuned two versions of Multilingual Universal Sentence Encoder (M-USE), Multilingual Bidirectional Encoder Representations from Transformers (M-BERT) and RuBERT for toxic comments detection in Russian. Fine-tuned RuBERT-Toxic achieved F<sub>1</sub> = 92.20%, demonstrating the best classification score.


## Toxic Comments Dataset
[Kaggle Russian Language Toxic Comments Dataset](https://www.kaggle.com/blackmoon/russian-language-toxic-comments) is the collection of Russian-language annotated comments from [2ch](https://2ch.hk/) and [Pikabu](https://pikabu.ru/), which was published on Kaggle in 2019. It consists of 14412 comments, where 4826 texts were labelled as toxic, and 9586 were labelled as non-toxic. The average length of comments is ~175 characters; the minimum length is 21, and the maximum is 7403. 

## Citation
If you find this repository helpful, feel free to cite our publication:

```
@INPROCEEDINGS{Smetanin2020Toxic,
  author={Sergey Smetanin},
  booktitle={Computational Linguistics and Intellectual Technologies: Proceedings of the International Conference “Dialogue 2020”},
  title={Toxic Comments Detection in Russian},
  year={2020},
  doi={10.28995/2075-7182-2020-19-1149-1159}
} 
```