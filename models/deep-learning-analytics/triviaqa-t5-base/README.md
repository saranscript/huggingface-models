---
language: "eng"
tags:
- triviaqa
- t5-base
- pytorch
- lm-head
- question-answering
- closed-book
- t5
- pipeline:question-answering
datasets:
- triviaqa 
widget:
- text: ["Mount Everest is found in which mountain range?","None"]
metrics:
- EM: 17
- Subset match: 24.5
---

# Model name
Closed Book Trivia-QA T5 base

## Model description

This is a T5-base model trained on No Context Trivia QA data set. The input to the model is a Trivia type question. The model is tuned to search for the answer in its memory to return it. The pretrained model used here was trained on Common Crawl (C4) data set. The model was trained for 135 epochs using a batch size of 32 and learning rate of 1e-3. Max_input_lngth is set as 25 and max_output_length is 10. Model attained an EM score of 17 and a Subset Match score of 24.5
We have written a blog post that covers the training procedure. Please find it [here](https://medium.com/@priya.dwivedi/build-a-trivia-bot-using-t5-transformer-345ff83205b6). 

Test the model on Trivia Questions from the websites below:
https://www.triviaquestionss.com/easy-trivia-questions/
https://laffgaff.com/easy-trivia-questions-and-answers/

## Usage

```
from transformers import AutoTokenizer, AutoModelWithLMHead

tokenizer = AutoTokenizer.from_pretrained("deep-learning-analytics/triviaqa-t5-base")
model = AutoModelWithLMHead.from_pretrained("deep-learning-analytics/triviaqa-t5-base")

device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
model = model.to(device)

text = "Who directed the movie Jaws?"

preprocess_text = text.strip().replace("\n","")
tokenized_text = tokenizer.encode(preprocess_text, return_tensors="pt").to(device)

outs = model.model.generate(
            tokenized_text,
            max_length=10,
            num_beams=2,
            early_stopping=True
           )

dec = [tokenizer.decode(ids) for ids in outs]
print("Predicted Answer: ", dec)
```
