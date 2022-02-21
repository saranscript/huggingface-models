# ehdwns1516/bert-base-uncased_SWAG

* This model has been trained as a [SWAG dataset](https://huggingface.co/ehdwns1516/bert-base-uncased_SWAG).

* Sentence Inference Multiple Choice DEMO: [Ainize DEMO](https://main-sentence-inference-multiple-choice-ehdwns1516.endpoint.ainize.ai/)

* Sentence Inference Multiple Choice API: [Ainize API](https://ainize.web.app/redirect?git_repo=https://github.com/ehdwns1516/sentence_inference_multiple_choice)

## Overview

Language model: [bert-base-uncased](https://huggingface.co/bert-base-uncased)

Language: English

Training data: [SWAG dataset](https://huggingface.co/datasets/swag)

Code: See [Ainize Workspace](https://ainize.ai/workspace/create?imageId=hnj95592adzr02xPTqss&git=https://github.com/ehdwns1516/Multiple_choice_SWAG_finetunning)

## Usage
## In Transformers

```
from transformers import AutoTokenizer, AutoModelForMultipleChoice
  
tokenizer = AutoTokenizer.from_pretrained("ehdwns1516/bert-base-uncased_SWAG")

model = AutoModelForMultipleChoice.from_pretrained("ehdwns1516/bert-base-uncased_SWAG")

def run_model(candicates_count, context: str, candicates: list[str]):
    assert len(candicates) == candicates_count, "you need " + candicates_count + " candidates"
    choices_inputs = []
    for c in candicates:
        text_a = ""  # empty context
        text_b = context + " " + c
        inputs = tokenizer(
            text_a,
            text_b,
            add_special_tokens=True,
            max_length=128,
            padding="max_length",
            truncation=True,
            return_overflowing_tokens=True,
        )
        choices_inputs.append(inputs)

    input_ids = torch.LongTensor([x["input_ids"] for x in choices_inputs])
    output = model(input_ids=input_ids)

    return {"result": candicates[torch.argmax(output.logits).item()]}

items = list()
count = 4 # candicates count
context = "your context"
for i in range(int(count)):
    items.append("sentence")

result = run_model(count, context, items)
```
