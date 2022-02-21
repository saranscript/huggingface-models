```python
from transformers import (
    AutoModelForSequenceClassification,
    AutoTokenizer,
)

model = AutoModelForSequenceClassification.from_pretrained("shahrukhx01/roberta-base-boolq")
model.to(device) 
#model.push_to_hub("roberta-base-boolq")

tokenizer = AutoTokenizer.from_pretrained("shahrukhx01/roberta-base-boolq")

def predict(question, passage):
  sequence = tokenizer.encode_plus(question, passage, return_tensors="pt")['input_ids'].to(device)
  
  logits = model(sequence)[0]
  probabilities = torch.softmax(logits, dim=1).detach().cpu().tolist()[0]
  proba_yes = round(probabilities[1], 2)
  proba_no = round(probabilities[0], 2)

  print(f"Question: {question}, Yes: {proba_yes}, No: {proba_no}")
  
passage = """Berlin is the capital and largest city of Germany by both area and population. Its 3.8 million inhabitants make it the European Union's most populous city, 
                        according to population within city limits."""
 
question = "Is Berlin the smallest city of Germany?"
predict(s_question, passage)
```