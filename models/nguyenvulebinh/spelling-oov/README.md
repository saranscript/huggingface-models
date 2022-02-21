```python
from transformers import EncoderDecoderModel
from importlib.machinery import SourceFileLoader
from transformers.file_utils import cached_path, hf_bucket_url
import torch
import os

## Load model & tokenizer
cache_dir='./cache'
model_name='nguyenvulebinh/spelling-oov'

def download_tokenizer_files():
    resources = ['envibert_tokenizer.py', 'dict.txt', 'sentencepiece.bpe.model']
    for item in resources:
        if not os.path.exists(os.path.join(cache_dir, item)):
            tmp_file = hf_bucket_url(model_name, filename=item)
            tmp_file = cached_path(tmp_file,cache_dir=cache_dir)
            os.rename(tmp_file, os.path.join(cache_dir, item))
        
download_tokenizer_files()
spell_tokenizer = SourceFileLoader("envibert.tokenizer",os.path.join(cache_dir,'envibert_tokenizer.py')).load_module().RobertaTokenizer(cache_dir)
spell_model = EncoderDecoderModel.from_pretrained(model_name)

def oov_spelling(word, num_candidate=1):
    result = []
    inputs = spell_tokenizer([word.lower()])
    input_ids = inputs['input_ids']
    attention_mask = inputs['attention_mask']
    inputs = {
        "input_ids": torch.tensor(input_ids),
        "attention_mask": torch.tensor(attention_mask)
    }
    outputs = spell_model.generate(**inputs, num_return_sequences=num_candidate)
    for output in outputs.cpu().detach().numpy().tolist():
        result.append(spell_tokenizer.sp_model.DecodePieces(spell_tokenizer.decode(output, skip_special_tokens=True).split()))
    return result    
    
oov_spelling('spacespeaker')
# output: ['x pây x pếch cơ']

```