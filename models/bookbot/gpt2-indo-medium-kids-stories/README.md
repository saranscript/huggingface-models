---
language: id
tags:
  - gpt2-indo-medium-kids-stories
license: mit
widget:
  - text: "Archie sedang mengendarai roket ke planet Mars."
---

## GPT-2 Indonesian Medium Kids Stories

GPT-2 Indonesian Medium Kids Stories is a causal language model based on the [OpenAI GPT-2](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) model. The model was originally the pre-trained [GPT2 Medium Indonesian](https://huggingface.co/flax-community/gpt2-medium-indonesian) model, which was then fine-tuned on Indonesian kids' stories from [Room To Read](https://literacycloud.org/) and [Let's Read](https://reader.letsreadasia.org/).

10% of the dataset was kept for evaluation purposes. The pre-trained model was fine-tuned and achieved an evaluation loss of 3.579 and an evaluation perplexity of 35.84.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                           | #params | Arch.       | Training/Validation data (text)   |
| ------------------------------- | ------- | ----------- | --------------------------------- |
| `gpt2-indo-medium-kids-stories` | 345M    | GPT2 Medium | Indonesian Kids' Stories (860 KB) |

## Evaluation Results

The model was fine-tuned for 3 epochs.

| Epoch | Training Loss | Validation Loss |
| ----- | ------------- | --------------- |
| 1     | 3.909100      | 3.627678        |
| 2     | 3.375300      | 3.562854        |
| 3     | 3.113300      | 3.578999        |

## How to Use (PyTorch)

### As Causal Language Model

```python
from transformers import pipeline

pretrained_name = "bookbot/gpt2-indo-medium-kids-stories"

nlp = pipeline(
    "text-generation",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("Archie sedang mengendarai roket ke planet Mars.")
```

### Feature Extraction in PyTorch

```python
from transformers import GPT2LMHeadModel, GPT2TokenizerFast

pretrained_name = "bookbot/gpt2-indo-medium-kids-stories"
model = GPT2LMHeadModel.from_pretrained(pretrained_name)
tokenizer = GPT2TokenizerFast.from_pretrained(pretrained_name)

prompt = "Archie sedang mengendarai roket ke planet Mars."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer

Do consider the biases which come from both the pre-trained GPT-2 model and the Indonesian Kids' Stories dataset that may be carried over into the results of this model.

## Author

GPT-2 Indonesian Medium Kids Stories was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.
