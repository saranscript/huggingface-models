# klue-roberta-base-kornli

* This model trained with Korean dataset.
* Input premise sentence and hypothesis sentence.
* You can use English, but don't expect accuracy.
* If the context is longer than 1200 characters, the context may be cut in the middle and the result may not come out well.

klue-roberta-base-kornli DEMO: [Ainize DEMO](https://main-klue-roberta-base-kornli-ehdwns1516.endpoint.ainize.ai/)

klue-roberta-base-kornli API: [Ainize API](https://ainize.web.app/redirect?git_repo=https://github.com/ehdwns1516/klue-roberta-base_kornli)

## Overview

Language model: [klue/roberta-base](https://huggingface.co/klue/roberta-base)

Language: Korean

Training data: [kakaobrain KorNLI](https://github.com/kakaobrain/KorNLUDatasets/tree/master/KorNLI)

Eval data: [kakaobrain KorNLI](https://github.com/kakaobrain/KorNLUDatasets/tree/master/KorNLI)

Code: See [Ainize Workspace](https://ainize.ai/workspace/create?imageId=hnj95592adzr02xPTqss&git=https://github.com/ehdwns1516/klue-roberta-base_finetunning_ex)

## Usage
## In Transformers

```
from transformers import AutoTokenizer, pipeline

tokenizer = AutoTokenizer.from_pretrained("ehdwns1516/klue-roberta-base-kornli")

classifier = pipeline(
    "text-classification",
    model="ehdwns1516/klue-roberta-base-kornli",
    return_all_scores=True,
)

premise = "your premise"
hypothesis = "your hypothesis"

result = dict()
result[0] = classifier(premise + tokenizer.sep_token + hypothesis)[0]
```
