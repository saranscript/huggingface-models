# keytotext

Idea is to build a model which will take keywords as inputs and generate sentences as outputs. 

### Model:

Two Models have been built: 

- Using T5-base size = 850 MB can be found here: https://huggingface.co/gagan3012/keytotext
- Using T5-small size = 230 MB can be found here: https://huggingface.co/gagan3012/keytotext-small

#### Usage:

```python
from transformers import AutoTokenizer, AutoModelWithLMHead

tokenizer = AutoTokenizer.from_pretrained("gagan3012/keytotext-small")

model = AutoModelWithLMHead.from_pretrained("gagan3012/keytotext-small")
```

### Demo:

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/gagan3012/keytotext/app.py)

https://share.streamlit.io/gagan3012/keytotext/app.py

![image](https://user-images.githubusercontent.com/49101362/110660053-3b20fe80-81d4-11eb-9275-ba402134e8d9.png)


### Example: 

['India', 'Wedding']  -> We are celebrating today in New Delhi with three wedding anniversary parties.
