---
language:
- en
tags:
- text2text-generation
license: mit
datasets:
- wikifactcheck
widget:
- text: "Little Miss Sunshine was filmed over 30 days."
---
# BART base negative claim generation model

This is a BART-based model fine-tuned for negative claim generation. This model is used in the data augmentation process described in the paper [CrossAug: A Contrastive Data Augmentation Method for Debiasing Fact Verification Models](https://arxiv.org/abs/2109.15107). The model has been fine-tuned using the parallel and opposing claims from WikiFactCheck-English dataset.

## Usage

```python
import torch
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

model_name = 'minwhoo/bart-base-negative-claim-generation'
tokenizer = AutoTokenizer.from_pretrained(model_name)

model = AutoModelForSeq2SeqLM.from_pretrained(model_name)
model.to('cuda' if torch.cuda.is_available() else 'cpu')

examples = [
    "Little Miss Sunshine was filmed over 30 days.",
    "Magic Johnson did not play for the Lakers.",
    "Claire Danes is wedded to an actor from England."
]

batch = tokenizer(examples, max_length=1024, padding=True, truncation=True, return_tensors="pt")
out = model.generate(batch['input_ids'].to(model.device), num_beams=5)
negative_examples = tokenizer.batch_decode(out, skip_special_tokens=True)
print(negative_examples)
# ['Little Miss Sunshine was filmed less than 3 days.', 'Magic Johnson played for the Lakers.', 'Claire Danes is married to an actor from France.']
```

## Citation

```
@inproceedings{lee2021crossaug,
  title={CrossAug: A Contrastive Data Augmentation Method for Debiasing Fact Verification Models},
  author={Minwoo Lee and Seungpil Won and Juae Kim and Hwanhee Lee and Cheoneum Park and Kyomin Jung},
  booktitle={Proceedings of the 30th ACM International Conference on Information & Knowledge Management},
  publisher={Association for Computing Machinery},
  series={CIKM '21},
  year={2021}
}
```