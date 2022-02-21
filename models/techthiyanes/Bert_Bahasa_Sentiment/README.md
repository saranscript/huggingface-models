from transformers import AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained(model_checkpoint)

model = AutoModelForSequenceClassification.from_pretrained('techthiyanes/Bert_Bahasa_Sentiment')

inputs = tokenizer("saya tidak", return_tensors="pt")

labels = torch.tensor([1]).unsqueeze(0) 

outputs = model(**inputs, labels=labels)

loss = outputs.loss

logits = outputs.logits

outputs
hello
