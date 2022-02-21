Converted for Tensorflow
```
!pip install transformers sentencepiece
from transformers import TFAutoModel, AutoTokenizer
name = "xlm-roberta-base"
model = TFAutoModel.from_pretrained(name, from_pt=True)
tokenizer = AutoTokenizer.from_pretrained(name)
model.save_pretrained("local-xlm-roberta-base")
tokenizer.save_pretrained("local-xlm-roberta-base")
```