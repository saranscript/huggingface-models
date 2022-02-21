---
language: "en"
tags:
- dstc10
- knowledge title-body validation
widget:
- text: "Can you accommodate large groups? It does not offer free WiFi."
- text: "Is there a gym on site? It does not have an onsite fitness center."
---
This is the model used for knowledge clustering where we feed title-body pair and the classifier predicts if the pair is valid or not.
For further information, please refer to https://github.com/yctam/dstc10_track2_task2 for the Github repository.

Credit: Jiakai Zou, Wilson Tam

---
```python
from transformers import AutoConfig, AutoTokenizer, AutoModelForSequenceClassification

def single_test(tokenizer, title_body_pair):
    result = tokenizer([title_body_pair], return_tensors="pt")
    model.eval()
    outputs = model(**result)
    predictions = outputs.logits.argmax(dim=-1)
    # There was a mistake in flipping the labels.
    return True if predictions == 0 else False

if __name__ == '__main__':
    model_name = "wilsontam/bert-base-uncased-dstc10-kb-title-body-validate"

    config = AutoConfig.from_pretrained(model_name)
    tokenizer = AutoTokenizer.from_pretrained(model_name, use_fast=True)
    model = AutoModelForSequenceClassification.from_pretrained(".")

    sentence = "Can I check in anytime?"
    body = "Yes, 24 Hours Front Desk Avaliable."
    print(single_test((sentence, body))) # Expect: True       
```