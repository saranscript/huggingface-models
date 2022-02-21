---
language: id
tags:
  - gpt2-indo-small-kids-stories
license: mit
widget:
  - text: "Archie sedang mengendarai roket ke planet Mars."
---

## GPT-2 Indonesian Small Kids Stories

GPT-2 Indonesian Small Kids Stories is a causal language model based on the [OpenAI GPT-2](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) model. The model was originally the pre-trained [GPT2 Small Indonesian](https://huggingface.co/flax-community/gpt2-small-indonesian) model, which was then fine-tuned on Indonesian kids' stories from [Room To Read](https://literacycloud.org/) and [Let's Read](https://reader.letsreadasia.org/).

10% of the dataset was kept for evaluation purposes. The pre-trained model was fine-tuned and achieved an evaluation loss of 3.777 and an evaluation perplexity of 43.68.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                          | #params | Arch.      | Training/Validation data (text)   |
| ------------------------------ | ------- | ---------- | --------------------------------- |
| `gpt2-indo-small-kids-stories` | 124M    | GPT2 Small | Indonesian Kids' Stories (860 KB) |

## Evaluation Results

The model was fine-tuned for 10 epochs.

| Epoch | Training Loss | Validation Loss |
| ----- | ------------- | --------------- |
| 1     | 4.259600      | 4.020201        |
| 2     | 3.979100      | 3.911295        |
| 3     | 3.818300      | 3.849313        |
| 4     | 3.691600      | 3.809931        |
| 5     | 3.589300      | 3.789201        |
| 6     | 3.506200      | 3.778665        |
| 7     | 3.439200      | 3.774871        |
| 8     | 3.387600      | 3.774859        |
| 9     | 3.351300      | 3.776672        |
| 10    | 3.330100      | 3.776935        |

## How to Use (PyTorch)

### As Causal Language Model

```python
from transformers import pipeline

pretrained_name = "bookbot/gpt2-indo-small-kids-stories"

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

pretrained_name = "bookbot/gpt2-indo-small-kids-stories"
model = GPT2LMHeadModel.from_pretrained(pretrained_name)
tokenizer = GPT2TokenizerFast.from_pretrained(pretrained_name)

prompt = "Archie sedang mengendarai roket ke planet Mars."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Disclaimer

Do consider the biases which come from both the pre-trained GPT-2 model and the Indonesian Kids' Stories dataset that may be carried over into the results of this model.

## Author

GPT-2 Indonesian Small Kids Stories was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.
