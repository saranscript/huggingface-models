Sample usage: 
```python 
tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
model = GPT2LMHeadModel.from_pretrained("danyaljj/gpt2_question_generation_given_paragraph_answer")
input_ids = tokenizer.encode("There are two apples on the counter. A: apples Q:", return_tensors="pt")
outputs = model.generate(input_ids)
print("Generated:", tokenizer.decode(outputs[0], skip_special_tokens=True))
```
Which should produce this: 
```
Generated: There are two apples on the counter. A: apples Q: What is the name of the counter
```