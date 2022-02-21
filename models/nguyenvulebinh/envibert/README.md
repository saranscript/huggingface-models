---
language: vi
tags:
- exbert
license: cc-by-nc-4.0
---

# RoBERTa for Vietnamese and English (envibert)

This RoBERTa version is trained by using 100GB of text (50GB of Vietnamese and 50GB of English) so it is named ***envibert***. The model architecture is custom for production so it only contains 70M parameters.

## Usages

```python
from transformers import RobertaModel
from transformers.file_utils import cached_path, hf_bucket_url
from importlib.machinery import SourceFileLoader
import os

cache_dir='./cache'
model_name='nguyenvulebinh/envibert'

def download_tokenizer_files():
  resources = ['envibert_tokenizer.py', 'dict.txt', 'sentencepiece.bpe.model']
  for item in resources:
    if not os.path.exists(os.path.join(cache_dir, item)):
      tmp_file = hf_bucket_url(model_name, filename=item)
      tmp_file = cached_path(tmp_file,cache_dir=cache_dir)
      os.rename(tmp_file, os.path.join(cache_dir, item))
      
download_tokenizer_files()
tokenizer = SourceFileLoader("envibert.tokenizer", os.path.join(cache_dir,'envibert_tokenizer.py')).load_module().RobertaTokenizer(cache_dir)
model = RobertaModel.from_pretrained(model_name,cache_dir=cache_dir)

# Encode text
text_input = 'Đại học Bách Khoa Hà Nội .'
text_ids = tokenizer(text_input, return_tensors='pt').input_ids
# tensor([[   0,  705,  131, 8751, 2878,  347,  477,    5,    2]])

# Extract features
text_features = model(text_ids)
text_features['last_hidden_state'].shape
# torch.Size([1, 9, 768])
len(text_features['hidden_states'])
# 7
```

### Citation

```text
@inproceedings{nguyen20d_interspeech,
  author={Thai Binh Nguyen and Quang Minh Nguyen and Thi Thu Hien Nguyen and Quoc Truong Do and Chi Mai Luong},
  title={{Improving Vietnamese Named Entity Recognition from Speech Using Word Capitalization and Punctuation Recovery Models}},
  year=2020,
  booktitle={Proc. Interspeech 2020},
  pages={4263--4267},
  doi={10.21437/Interspeech.2020-1896}
}
```
**Please CITE** our repo when it is used to help produce published results or is incorporated into other software.


# Contact 

nguyenvulebinh@gmail.com

[![Follow](https://img.shields.io/twitter/follow/nguyenvulebinh?style=social)](https://twitter.com/intent/follow?screen_name=nguyenvulebinh)