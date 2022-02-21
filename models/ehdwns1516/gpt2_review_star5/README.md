# gpt2_review_star5

* This model has been trained as a review_body dataset with a star of 5 in the [amazon_review dataset](https://huggingface.co/datasets/amazon_reviews_multi).
* Input text what you want to generate review.
* If the context is longer than 1200 characters, the context may be cut in the middle and the result may not come out well.

review generator DEMO: [Ainize DEMO](https://main-review-generator-ehdwns1516.endpoint.ainize.ai/)

review generator API: [Ainize API](https://ainize.web.app/redirect?git_repo=https://github.com/ehdwns1516/review_generator)

## Model links for each 1 to 5 star
* [ehdwns1516/gpt2_review_star1](https://huggingface.co/ehdwns1516/gpt2_review_star1)
* [ehdwns1516/gpt2_review_star2](https://huggingface.co/ehdwns1516/gpt2_review_star2)
* [ehdwns1516/gpt2_review_star3](https://huggingface.co/ehdwns1516/gpt2_review_star3)
* [ehdwns1516/gpt2_review_star4](https://huggingface.co/ehdwns1516/gpt2_review_star4)
* [ehdwns1516/gpt2_review_star5](https://huggingface.co/ehdwns1516/gpt2_review_star5)

## Overview

Language model: [gpt2](https://huggingface.co/gpt2)

Language: English

Training data: review_body dataset with a star of 5 in the [amazon_review dataset](https://huggingface.co/datasets/amazon_reviews_multi).

Code: See [Ainize Workspace](https://ainize.ai/workspace/create?imageId=hnj95592adzr02xPTqss&git=https://github.com/ehdwns1516/gpt2_review_fine-tunning_note)

## Usage
## In Transformers

```
from transformers import AutoTokenizer, AutoModelWithLMHead
  
tokenizer = AutoTokenizer.from_pretrained("ehdwns1516/gpt2_review_star5")

model = AutoModelWithLMHead.from_pretrained("ehdwns1516/gpt2_review_star5")

generator = pipeline(
    "text-generation",
    model="ehdwns1516/gpt2_review_star5",
    tokenizer=tokenizer
)

context = "your context"

result = dict()
result[0] = generator(context)[0]
```
