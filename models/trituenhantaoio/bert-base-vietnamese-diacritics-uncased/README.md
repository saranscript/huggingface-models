## Usage
```python
from transformers import BertForSequenceClassification
from transformers import BertTokenizer
model = BertForSequenceClassification.from_pretrained("trituenhantaoio/bert-base-vietnamese-diacritics-uncased")
tokenizer = BertTokenizer.from_pretrained("trituenhantaoio/bert-base-vietnamese-diacritics-uncased")
```

### References

```
@article{ttnt2020bertdiacritics,
  title={Vietnamese BERT Diacritics: Pretrained on News and Wiki},
  author={trituenhantao.io},
  year = {2020},
  publisher = {Hugging Face},
  journal = {Hugging Face repository}
}
```

[trituenhantao.io](https://trituenhantao.io)