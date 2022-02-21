# language:

- en
- zu

#  license:

- apache-2.0

# tags:

- Translation
- Text2Text Generation

# datasets:

## Pre-trained on:

- MarianMT English - isiXhosa
- Dataset: OPUS (https://opus.nlpl.eu/)

## Fine-tuned on:

- Umsuka English - isiZulu Parallel Corpus (https://zenodo.org/record/5035171#.YZ39iNBBy3A)

# metrics

- BLEU

# Usage:


```
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
  
tokenizer = AutoTokenizer.from_pretrained("MUNasir/opus-en-xh-umsuka-en-zu")

model = AutoModelForSeq2SeqLM.from_pretrained("MUNasir/opus-en-xh-umsuka-en-zu")
```

OR download the repo:

```
git lfs install
git clone https://huggingface.co/MUNasir/opus-en-xh-umsuka-en-zu
# if you want to clone without large files – just their pointers
# prepend your git clone with the following env var:
GIT_LFS_SKIP_SMUDGE=1
```

# Benchmarks


| Corpus                 | BLEU (dev)                                                   |      BLEU (test)                          |                                                             
|----------------------|-----------------------------------------------------------|------------------------------------------------|
| Umsuka                 | 15.4806                                                    | 13.042  



# Main Contributors:

| Name                 | GitHub                                                    | Social                                                                                              |
|----------------------|-----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| Muhammad Umair Nasir | [umair-nasir14](https://github.com/umair-nasir14)         | [Linkedin](https://www.linkedin.com/in/umair-nasir/) \| [Twitter](https://twitter.com/utheprodigyn) |
| Samantha Ball        | [SamBall999](https://github.com/SamBall999)               | -                                                                                                   |
| Innocent Mchechesi   | [InnocentMchechesi](https://github.com/InnocentMchechesi) | -                                                                                                   |
# GitHub repo:

https://github.com/umair-nasir14/English-Zulu-MarianMT-Model
