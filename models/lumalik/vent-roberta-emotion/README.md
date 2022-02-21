# Vent-roBERTa-emotion

This is a roBERTa pretrained on twitter and then trained for self-labeled emotion classification on the Vent dataset (see https://arxiv.org/abs/1901.04856). The Vent dataset contains 33 million posts annotated with one emotion by the user themselves. <br/>
   
The model was trained to recognize 5 emotions ("Affection", "Anger", "Fear", "Happiness", "Sadness") on 7 million posts from the dataset. <br/>

Example of how to use the classifier on single texts. <br/>

```` 
from transformers import AutoModelForSequenceClassification
from transformers import AutoTokenizer
import numpy as np
from scipy.special import softmax
import torch

tokenizer = AutoTokenizer.from_pretrained("lumalik/vent-roberta-emotion")
model = AutoModelForSequenceClassification.from_pretrained("lumalik/vent-roberta-emotion")
model.eval()

texts = ["You wont believe what happened to me today",
         "You wont believe what happened to me today!",
         "You wont believe what happened to me today...",
         "You wont believe what happened to me today <3",
         "You wont believe what happened to me today :)",
         "You wont believe what happened to me today :("]

for text in texts:
    encoded_text = tokenizer(text, return_tensors="pt")

    output = model(**encoded_text)

    output = softmax(output[0].detach().numpy(), axis=1)

    print("======================")
    print(text)
    print("Affection: {}".format(output[0][0]))
    print("Anger: {}".format(output[0][1]))
    print("Fear: {}".format(output[0][2]))
    print("Happiness: {}".format(output[0][3]))
    print("Sadness: {}".format(output[0][4]))
```` 