---
language: 
- en
tags:
- text-classification
- zero-shot-classification
metrics:
- accuracy
datasets:
- multi_nli
- anli
- fever
pipeline_tag: zero-shot-classification

---
# DeBERTa-v3-base-mnli-fever-anli
## Model description
This model was trained on the MultiNLI, Fever-NLI and Adversarial-NLI (ANLI) datasets, which comprise 763 913 NLI hypothesis-premise pairs. This base model outperforms almost all large models on the [ANLI benchmark](https://github.com/facebookresearch/anli). 
The base model is [DeBERTa-v3-base from Microsoft](https://huggingface.co/microsoft/deberta-v3-base). The v3 variant of DeBERTa substantially outperforms previous versions of the model by including a different pre-training objective, see annex 11 of the original [DeBERTa paper](https://arxiv.org/pdf/2006.03654.pdf). 

## Intended uses & limitations
#### How to use the model
```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch

model_name = "MoritzLaurer/DeBERTa-v3-base-mnli-fever-anli"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name)

premise = "I first thought that I liked the movie, but upon second thought it was actually disappointing."
hypothesis = "The movie was good."

input = tokenizer(premise, hypothesis, truncation=True, return_tensors="pt")
output = model(input["input_ids"].to(device))  # device = "cuda:0" or "cpu"
prediction = torch.softmax(output["logits"][0], -1).tolist()
label_names = ["entailment", "neutral", "contradiction"]
prediction = {name: round(float(pred) * 100, 1) for pred, name in zip(prediction, label_names)}
print(prediction)
```
### Training data
DeBERTa-v3-base-mnli-fever-anli was trained on the MultiNLI, Fever-NLI and Adversarial-NLI (ANLI) datasets, which comprise 763 913 NLI hypothesis-premise pairs.

### Training procedure
DeBERTa-v3-base-mnli-fever-anli was trained using the Hugging Face trainer with the following hyperparameters.
```
training_args = TrainingArguments(
    num_train_epochs=3,              # total number of training epochs
    learning_rate=2e-05,
    per_device_train_batch_size=32,   # batch size per device during training
    per_device_eval_batch_size=32,    # batch size for evaluation
    warmup_ratio=0.1,                # number of warmup steps for learning rate scheduler
    weight_decay=0.06,               # strength of weight decay
    fp16=True                        # mixed precision training
)
```
### Eval results
The model was evaluated using the test sets for MultiNLI and ANLI and the dev set for Fever-NLI. The metric used is accuracy.

mnli-m | mnli-mm | fever-nli | anli-all | anli-r3
---------|----------|---------|----------|----------
0.903 | 0.903 | 0.777 | 0.579 | 0.495

## Limitations and bias
Please consult the original DeBERTa paper and literature on different NLI datasets for potential biases. 

### BibTeX entry and citation info
If you want to cite this model, please cite the original DeBERTa paper, the respective NLI datasets and include a link to this model on the Hugging Face hub. 

### Ideas for cooperation or questions?
If you have questions or ideas for cooperation, contact me at m{dot}laurer{at}vu{dot}nl or [LinkedIn](https://www.linkedin.com/in/moritz-laurer/)

### Debugging and issues
Note that DeBERTa-v3 was released recently and older versions of HF Transformers seem to have issues running the model (e.g. resulting in an issue with the tokenizer). Using Transformers==4.13 might solve some issues. 
