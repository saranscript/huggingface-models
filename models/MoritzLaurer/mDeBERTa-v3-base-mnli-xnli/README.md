---
language: 
- multilingual
- en 
- ar 
- bg 
- de 
- el 
- es 
- fr 
- hi 
- ru 
- sw 
- th 
- tr 
- ur 
- vu 
- zh 
tags:
- zero-shot-classification
- text-classification
- nli
- pytorch
metrics:
- accuracy
datasets:
- multi_nli
- xnli
pipeline_tag: zero-shot-classification
widget:
- text: "Angela Merkel ist eine Politikerin in Deutschland und Vorsitzende der CDU"
  candidate_labels: "politics, economy, entertainment, environment"
---
# Multilingual mDeBERTa-v3-base-mnli-xnli
## Model description
This multilingual model can perform natural language inference (NLI) on 100 languages and is therefore also suitable for multilingual zero-shot classification. The underlying model was pre-trained by Microsoft on the [CC100 multilingual dataset](https://huggingface.co/datasets/cc100). It was then fine-tuned on the [XNLI dataset](https://huggingface.co/datasets/xnli), which contains hypothesis-premise pairs from 15 languages, as well as the English [MNLI dataset](https://huggingface.co/datasets/multi_nli).
As of December 2021, mDeBERTa-base is the best performing multilingual transformer (base) model, introduced by Microsoft in [this paper](https://arxiv.org/pdf/2111.09543.pdf). 


## Intended uses & limitations
#### How to use the model
```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch

model_name = "MoritzLaurer/mDeBERTa-v3-base-mnli-xnli"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name)

premise = "Angela Merkel ist eine Politikerin in Deutschland und Vorsitzende der CDU"
hypothesis = "Emmanuel Macron is the President of France"

input = tokenizer(premise, hypothesis, truncation=True, return_tensors="pt")
output = model(input["input_ids"].to(device))  # device = "cuda:0" or "cpu"
prediction = torch.softmax(output["logits"][0], -1).tolist()

label_names = ["entailment", "neutral", "contradiction"]
prediction = {name: round(float(pred) * 100, 1) for pred, name in zip(prediction, label_names)}

print(prediction)
```

### Training data
This model was trained on the XNLI development dataset and the MNLI train dataset. The XNLI development set consists of 5010 professionally translated texts for each of 15 languages (see [this paper](https://arxiv.org/pdf/1809.05053.pdf)). Note that the XNLI contains a training set of 15 machine translated versions of the MNLI dataset for 15 languages, but due to quality issues with these machine translations, this model was only trained on the professional translations from the XNLI development set and the original English MNLI training set (392 702 texts). Not using machine translated texts can avoid overfitting the model to the 15 languages; avoids catastrophic forgetting of the other 85 languages mDeBERTa was pre-trained on; and significantly reduces training costs. 

### Training procedure
DeBERTa-v3-base-mnli was trained using the Hugging Face trainer with the following hyperparameters.
```
training_args = TrainingArguments(
    num_train_epochs=2,              # total number of training epochs
    learning_rate=2e-05,
    per_device_train_batch_size=16,   # batch size per device during training
    per_device_eval_batch_size=16,    # batch size for evaluation
    warmup_ratio=0.1,                # number of warmup steps for learning rate scheduler
    weight_decay=0.06,               # strength of weight decay
)
```
### Eval results
The model was evaluated on the XNLI test set on 15 languages. Note that multilingual NLI models are capable of classifying NLI texts without receiving NLI training data in the specific language (cross-lingual transfer). This means that the model is also able of doing NLI on the other 85 languages mDeBERTa was training on, but performance is most likely lower than for those languages available in XNLI.

Also note that if other multilingual models on the model hub claim performance of around 90% on languages other than English, the authors have most likely made a mistake during testing since non of the latest papers shows a multilingual average performance of more than a few points above 80% on XNLI (see [here](https://arxiv.org/pdf/2111.09543.pdf) or [here](https://arxiv.org/pdf/1911.02116.pdf)). 

average | ar | bg | de | el | en | es | fr | hi | ru | sw | th | tr | ur | vu | zh 
---------|----------|---------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------
0.808 | 0.802 | 0.829 | 0.825 | 0.826 | 0.883 | 0.845 | 0.834 | 0.771 | 0.813 | 0.748 | 0.793 | 0.807 | 0.740 | 0.795 | 0.8116


## Limitations and bias
Please consult the original DeBERTa-V3 paper and literature on different NLI datasets for potential biases. 
### BibTeX entry and citation info
If you want to cite this model, please cite the original DeBERTa paper, the respective NLI datasets and include a link to this model on the Hugging Face hub. 

### Ideas for cooperation or questions?
If you have questions or ideas for cooperation, contact me at m{dot}laurer{at}vu{dot}nl or [LinkedIn](https://www.linkedin.com/in/moritz-laurer/)

### Debugging and issues
Note that DeBERTa-v3 was released recently and older versions of HF Transformers seem to have issues running the model (e.g. resulting in an issue with the tokenizer). Using Transformers==4.13 might solve some issues. Note that mDeBERTa currently does not support FP16, see here: https://github.com/microsoft/DeBERTa/issues/77