# PrivBERT 
PrivBERT is a privacy policy language model. We pre-trained PrivBERT on ~1 million privacy policies starting with the pretrained Roberta model. The data is available at [https://privaseer.ist.psu.edu/data](https://privaseer.ist.psu.edu/data)

## Usage
```
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("mukund/privbert")
model = AutoModel.from_pretrained("mukund/privbert")
```

## License 
If you use this dataset in research, you must cite the below paper.
```
Mukund Srinath, Shomir Wilson and C. Lee Giles. Privacy at Scale: Introducing the PrivaSeer Corpus of Web Privacy Policies. In Proc. ACL 2021.
```
For research, teaching, and scholarship purposes, the model is available under a CC BY-NC-SA license. Please contact us for any requests regarding commercial use.
