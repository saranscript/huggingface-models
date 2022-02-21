Converted for Tensorflow

```
!pip install transformers sentencepiece
from transformers import TFAutoModel, AutoTokenizer
name = "ai4bharat/indic-bert"
model = TFAutoModel.from_pretrained(name, from_pt=True)
tokenizer = AutoTokenizer.from_pretrained(name)
model.save_pretrained("local-indic-bert")
tokenizer.save_pretrained("local-indic-bert")
```
