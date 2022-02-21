# klue-roberta-base-sae

* This model trained with Korean dataset.
* Input sentence what you want to grasp intent.
* You can use English, but don't expect accuracy.

klue-roberta-base-kornli DEMO: [Ainize DEMO](https://main-klue-roberta-base-kornli-ehdwns1516.endpoint.ainize.ai/)

klue-roberta-base-kornli API: [Ainize API](https://ainize.web.app/redirect?git_repo=https://github.com/ehdwns1516/KLUE-RoBERTa-base_sae)

## Overview

Language model: [klue/roberta-base](https://huggingface.co/klue/roberta-base)

Language: Korean

Training data: [kor_sae](https://huggingface.co/datasets/kor_sae)

Eval data: [kor_sae](https://huggingface.co/datasets/kor_sae)

Code: See [Ainize Workspace](https://ainize.ai/workspace/create?imageId=hnj95592adzr02xPTqss&git=https://github.com/ehdwns1516/KLUE-RoBERTa-base_sae_notebook)

## Usage
## In Transformers

```
from transformers import AutoTokenizer, pipeline

tokenizer = AutoTokenizer.from_pretrained("ehdwns1516/klue-roberta-base-sae")

classifier = pipeline(
    "text-classification",
    model="ehdwns1516/klue-roberta-base-kornli",
    return_all_scores=True,
)

context = "sentence what you want to grasp intent"

result = dict()
result[0] = classifier(context)[0]
```
