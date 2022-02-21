---
language: 
  - zh
license: apache-2.0
widget:
- text: "生活的真谛是[MASK]。"
---
# Zhouwenwang-1.3B model (Chinese)，one model of [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM).
Zhouwenwang-1.3B apply a new unified structure, and jointly developed by the IDEA-CCNL and Zhuiyi Technology. In the pre-training, the model considers LM (Language Model) and MLM (Mask Language Model) tasks uniformly, and adds rotational position coding, so that the model has the ability to generate and understand. Zhouwenwang-1.3B is the largest model for LM and MLM tasks in the Chinese field. It will continue to be optimized in the direction of model scale, knowledge integration, and supervision task assistance.

## Usage
There is no structure of Zhouwenwang-1.3B in [Transformers](https://github.com/huggingface/transformers), you can run follow code to get structure of Zhouwenwang-1.3B from [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM)

 ```shell
 git clone https://github.com/IDEA-CCNL/Fengshenbang-LM.git
 ```

### Load model
```python
from model.roformer.modeling_roformer import RoFormerModel    
from model.roformer.configuration_roformer import RoFormerConfig
from transformers import BertTokenizer

tokenizer = BertTokenizer.from_pretrained("IDEA-CCNL/Zhouwenwang-1.3B")
config = RoFormerConfig.from_pretrained("IDEA-CCNL/Zhouwenwang-1.3B")
model = RoFormerModel.from_pretrained("IDEA-CCNL/Zhouwenwang-1.3B")


```
### Generate task
You can use Zhouwenwang-1.3B to continue writing

```python
from model.roformer.modeling_roformer import RoFormerModel
from transformers import AutoTokenizer
import torch
import numpy as np

sentence = '清华大学位于'
max_length = 32

tokenizer = AutoTokenizer.from_pretrained("IDEA-CCNL/Zhouwenwang-1.3B")
model = RoFormerModel.from_pretrained("IDEA-CCNL/Zhouwenwang-1.3B")

for i in range(max_length):
    encode = torch.tensor(
        [[tokenizer.cls_token_id]+tokenizer.encode(sentence, add_special_tokens=False)]).long()
    logits = model(encode)[0]
    logits = torch.nn.functional.linear(
        logits, model.embeddings.word_embeddings.weight)
    logits = torch.nn.functional.softmax(
        logits, dim=-1).cpu().detach().numpy()[0]
    sentence = sentence + \
        tokenizer.decode(int(np.random.choice(logits.shape[1], p=logits[-1])))
    if sentence[-1] == '。':
        break
print(sentence)
```

## Scores on downstream chinese tasks (without any data augmentation)
|     Model| afqmc    |  tnews  | iflytek    |  ocnli  |  cmnli  | wsc  | csl  |
| :--------:    | :-----:  | :----:  | :-----:   | :----: | :----: | :----: | :----: |
| roberta-wwm-ext-large | 0.7514      |   0.5872    | 0.6152      |   0.777    | 0.814    | 0.8914    | 0.86    |
| Zhouwenwang-1.3B | 0.7463     |   0.6036    | 0.6288     |   0.7654   | 0.7741    | 0.8849    | 0. 8777   |

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