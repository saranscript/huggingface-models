---
language: 
  - "hn"
  - "bn"
  - "mn"
tags:
- Text Classification

license: 	wtfpl
datasets:
- ComMA
metrics:
- F1-Score
widget:
- text: "but who in the holy hell says to relate with it,or inspired by it😂😂,i'm a 23 yr old student,and i say it's wrong,watch for entertainment purpose,and those who get inspired by such movies,its their mental problem.and all the praise that shahid's getting is for dark charachter that he portrays.and those sittis she's talking abt,don't we hear those when a villian arrives on [screen.my](http://screen.my/) point is bash sexism,whether it's by a man or a group of woman.and as far as i remember,those girls were not shown as dark characters,as kabir singh is🙂"
- text: "सही है, बोलने के अधिकार पर गाली दो, parotest के अधिकार पर पुलिश का सर फोड़ो ,मादरचोदो अधिकारो का कब सही इस्तेमाल करोगें🐷🐷🐷😠😠😠🖕"
---
# Automatic Identification of Gender Bias in Hindi,Bengali,Meitei Codemixed Texts

This is a XLM-Align-Base model trained on CoMMA dataset of 12k samples

-  This is an extension from our previous paper: [Hypers at ComMA@ICON: Modelling Aggressiveness, Gender Bias and Communal Bias Identification](https://arxiv.org/abs/2112.15417).

## Example Usage

```python
import torch
import numpy as np
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline
from transformers import set_seed

set_seed(425)

text = "some gender biased text"
pipe = pipeline("text-classification", model="seanbenhur/MuLTiGENBiaS")


def predict_pipe(text):
    prediction = pipe(text, return_all_scores=True)[0]
    return prediction


if __name__ == "__main__":
  target = predict_pipe(text)
  print(target)
  
 ```
 
 
 ### Some concerns
 - Note: The model is trained on relatively lower samples (i.e 12k) but with mix of four languages Hindi, Bengali, Meitei, and English. It contains both native on codemixed scripts, So the model might perform poorly on many text samples and might not generalize well.
 