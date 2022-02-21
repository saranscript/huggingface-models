# CoText (1-CC)

## Introduction
Paper: [CoTexT: Multi-task Learning with Code-Text Transformer](https://aclanthology.org/2021.nlp4prog-1.5.pdf)

Authors: _Long Phan, Hieu Tran, Daniel Le, Hieu Nguyen, James Anibal, Alec Peltekian, Yanfang Ye_

## How to use
For more details, do check out [our Github repo](https://github.com/justinphan3110/CoTexT). 
```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
​
tokenizer = AutoTokenizer.from_pretrained("razent/cotext-1-cc")  
model = AutoModelForSeq2SeqLM.from_pretrained("razent/cotext-1-cc")
​
sentence = "def add(a, b): return a + b"
text =  "python: " + sentence + " </s>"

encoding = tokenizer.encode_plus(text, pad_to_max_length=True, return_tensors="pt")
input_ids, attention_masks = encoding["input_ids"].to("cuda"), encoding["attention_mask"].to("cuda")

outputs = model.generate(
    input_ids=input_ids, attention_mask=attention_masks,
    max_length=256,
    early_stopping=True
)

for output in outputs:
    line = tokenizer.decode(output, skip_special_tokens=True, clean_up_tokenization_spaces=True)
    print(line)
```

## Citation
```
@inproceedings{phan-etal-2021-cotext,
    title = "{C}o{T}ex{T}: Multi-task Learning with Code-Text Transformer",
    author = "Phan, Long  and
      Tran, Hieu  and
      Le, Daniel  and
      Nguyen, Hieu  and
      Annibal, James  and
      Peltekian, Alec  and
      Ye, Yanfang",
    booktitle = "Proceedings of the 1st Workshop on Natural Language Processing for Programming (NLP4Prog 2021)",
    month = aug,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.nlp4prog-1.5",
    doi = "10.18653/v1/2021.nlp4prog-1.5",
    pages = "40--47"
}
```