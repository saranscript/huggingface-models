# ehdwns1516/bart_finetuned_xsum

* This model has been trained as a [xsum dataset](https://huggingface.co/datasets/xsum).
* Input text what you want to summarize.

review generator DEMO: [Ainize DEMO](https://main-text-summarizer-ehdwns1516.endpoint.ainize.ai/)

review generator API: [Ainize API](https://ainize.web.app/redirect?git_repo=https://github.com/ehdwns1516/text_summarizer)

## Overview

Language model: [facebook/bart-large](https://huggingface.co/facebook/bart-large)

Language: English

Training data: [xsum dataset](https://huggingface.co/datasets/xsum)

Code: See [Ainize Workspace](https://ainize.ai/workspace/create?imageId=hnj95592adzr02xPTqss&git=https://github.com/ehdwns1516/bart_finetuned_xsum-notebook)

## Usage
## In Transformers

```
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
  
tokenizer = AutoTokenizer.from_pretrained("ehdwns1516/bart_finetuned_xsum")

model = AutoModelForSeq2SeqLM.from_pretrained("ehdwns1516/bart_finetuned_xsum")

summarizer = pipeline(
    "summarization",
    model="ehdwns1516/bart_finetuned_xsum",
    tokenizer=tokenizer
)

context = "your context"

result = dict()
result[0] = summarizer(context)[0]
```
