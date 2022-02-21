---
language: 
  - zh
license: apache-2.0

inference: false

---
# Erlangshen-1.3B model (Chinese)，one model of [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM).
Encoder structure-based Bidirection language model, focusing on solving various natural language understanding tasks. The 1.3 billion parameter Erlangshen-1.3B large model, using 280G Chinese data, 32 A100 training for 14 days, is the largest open source Chinese Bert large model. On November 10, 2021, **it reached the top of the [FewCLUE](https://www.cluebenchmarks.com/fewclue.html)** list of the authoritative benchmark for Chinese language understanding. 

[IDEA研究院中文预训练模型二郎神登顶FewCLUE榜单](https://mp.weixin.qq.com/s/bA_9n_TlBE9P-UzCn7mKoA)

Among them, **CHID (Idiom Fill in the Blank) and TNEWS (News Classification) surpass human beings, CHID (Idiom Fill in the Blank), CSLDCP (Subject Document Classification), OCNLI (Natural Language Reasoning) single task first, refreshing few-shot learning records**. The Erlangshen series will continue to be optimized in terms of model scale, knowledge integration, and supervision task assistance.

## Usage
```python
from transformers import MegatronBertConfig, MegatronBertModel
from transformers import BertTokenizer

tokenizer = BertTokenizer.from_pretrained("IDEA-CCNL/Erlangshen-1.3B")
config = MegatronBertConfig.from_pretrained("IDEA-CCNL/Erlangshen-1.3B")
model = MegatronBertModel.from_pretrained("IDEA-CCNL/Erlangshen-1.3B")

```
## Scores on downstream chinese tasks (without any data augmentation)
|    Model   | afqmc    |  tnews  | iflytek    |  ocnli  |  cmnli  | wsc  | csl  |
| :--------:    | :-----:  | :----:  | :-----:   | :----: | :----: | :----: | :----: |
| roberta-wwm-ext-large | 0.7514      |   0.5872    | 0.6152      |   0.777    | 0.814    | 0.8914    | 0.86    |
| Erlangshen-1.3B | 0.7608      |   0.5996    | 0.6234      |   0.7917    | 0.81    | 0.9243    | 0.872    |

## Citation
If you find the resource is useful, please cite the following website in your paper.
```
@misc{Fengshenbang-LM,
  title={Fengshenbang-LM},
  author={IDEA-CCNL},
  year={2021},
  howpublished={\url{https://github.com/IDEA-CCNL/Fengshenbang-LM}},
}
```