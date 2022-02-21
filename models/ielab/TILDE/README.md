Please treat TILDE as a BertLMHeadModel model:
```
from transformers import BertLMHeadModel, BertTokenizerFast

model = BertLMHeadModel.from_pretrained("ielab/TILDE")
tokenizer = BertTokenizerFast.from_pretrained('bert-base-uncased')
```

Github: https://github.com/ielab/TILDE