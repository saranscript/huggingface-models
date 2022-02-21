---
language: 
  - zh
license: apache-2.0
widget:
- text: "生活的真谛是[MASK]。"
---
# Zhouwenwang-110M model (Chinese)，one model of [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM).
Zhouwenwang-110M apply a new unified structure, and jointly developed by the IDEA-CCNL and Zhuiyi Technology. In the pre-training, the model considers LM (Language Model) and MLM (Mask Language Model) tasks uniformly, and adds rotational position coding, so that the model has the ability to generate and understand. Zhouwenwang-110M is the largest model for LM and MLM tasks in the Chinese field. It will continue to be optimized in the direction of model scale, knowledge integration, and supervision task assistance.

## Usage
There is no structure of Zhouwenwang-110M in [Transformers](https://github.com/huggingface/transformers), you can run follow code to get structure of Zhouwenwang-110M from [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM)

 ```shell
 git clone https://github.com/IDEA-CCNL/Fengshenbang-LM.git
 ```

### Load Model
```python
from model.roformer.modeling_roformer import RoFormerModel    
from model.roformer.configuration_roformer import RoFormerConfig
from transformers import BertTokenizer

tokenizer = BertTokenizer.from_pretrained("IDEA-CCNL/Zhouwenwang-110M")
config = RoFormerConfig.from_pretrained("IDEA-CCNL/Zhouwenwang-110M")
model = RoFormerModel.from_pretrained("IDEA-CCNL/Zhouwenwang-110M")


```

### Generate task
You can use Zhouwenwang-110M to continue writing

```python
from model.roformer.modeling_roformer import RoFormerModel
from transformers import AutoTokenizer
import torch
import numpy as np

sentence = '清华大学位于'
max_length = 32

tokenizer = AutoTokenizer.from_pretrained("IDEA-CCNL/Zhouwenwang-110M")
model = RoFormerModel.from_pretrained("IDEA-CCNL/Zhouwenwang-110M")

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