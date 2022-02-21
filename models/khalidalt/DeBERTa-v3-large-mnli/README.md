---

language: 

- en

tags:

- text-classification

- zero-shot-classification

metrics:

- accuracy

widget:

- text: "The Movie have been criticized for the story. However, I think it is a great movie. [SEP] I liked the movie."

---

# DeBERTa-v3-large-mnli

## Model description

This model was trained on the Multi-Genre Natural Language Inference ( MultiNLI ) dataset, which consists of 433k sentence pairs textual entailment information. 

The model used is [DeBERTa-v3-large from Microsoft](https://huggingface.co/microsoft/deberta-large). The v3 DeBERTa outperforms the result of Bert and RoBERTa in  majority of NLU benchmarks by using disentangled attention and enhanced mask decoder. More information about the orginal model is on [official repository](https://github.com/microsoft/DeBERTa) and the [paper](https://arxiv.org/abs/2006.03654)

## Intended uses & limitations

#### How to use the model

```python

premise = "The Movie have been criticized for the story. However, I think it is a great movie."

hypothesis = "I liked the movie."

input = tokenizer(premise, hypothesis, truncation=True, return_tensors="pt")

output = model(input["input_ids"].to(device))  # device = "cuda:0" or "cpu"

prediction = torch.softmax(output["logits"][0], -1)

label_names = ["entailment", "neutral", "contradiction"]

print(label_names[prediction.argmax(0).tolist()])

```

### Training data

This model was trained on the MultiNLI dataset, which consists of 392K sentence textual entitlement. 

### Training procedure

DeBERTa-v3-large-mnli was trained using the Hugging Face trainer with the following hyperparameters.

```

train_args = TrainingArguments(
    learning_rate=2e-5,
    
    per_device_train_batch_size=8,
    
    per_device_eval_batch_size=8,
    
    num_train_epochs=3,
    
    warmup_ratio=0.06,  
    
    weight_decay=0.1, 
    
    fp16=True,
    
    seed=42,
)



```

### BibTeX entry and citation info

Please cite the [DeBERTa paper](https://arxiv.org/abs/2006.03654) and [MultiNLI Dataset](https://cims.nyu.edu/~sbowman/multinli/paper.pdf) if you use this model and include this Huggingface hub. 