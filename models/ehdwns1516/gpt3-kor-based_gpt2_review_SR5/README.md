# ehdwns1516/gpt3-kor-based_gpt2_review_SR5

* This model has been trained Korean dataset as a star of 5 in the [naver shopping reivew dataset](https://github.com/bab2min/corpus/tree/master/sentiment).
* Input text what you want to generate review.
* If the context is longer than 1200 characters, the context may be cut in the middle and the result may not come out well.

review generator DEMO: [Ainize DEMO](https://main-review-generator-ehdwns1516.endpoint.ainize.ai/)

review generator API: [Ainize API](https://ainize.web.app/redirect?git_repo=https://github.com/ehdwns1516/review_generator)

## Model links for each 1 to 5 star
* [ehdwns1516/gpt3-kor-based_gpt2_review_SR1](https://huggingface.co/ehdwns1516/gpt3-kor-based_gpt2_review_SR1)
* [ehdwns1516/gpt3-kor-based_gpt2_review_SR2](https://huggingface.co/ehdwns1516/gpt3-kor-based_gpt2_review_SR2)
* [ehdwns1516/gpt3-kor-based_gpt2_review_SR3](https://huggingface.co/ehdwns1516/gpt3-kor-based_gpt2_review_SR3)
* [ehdwns1516/gpt3-kor-based_gpt2_review_SR4](https://huggingface.co/ehdwns1516/gpt3-kor-based_gpt2_review_SR4)
* [ehdwns1516/gpt3-kor-based_gpt2_review_SR5](https://huggingface.co/ehdwns1516/gpt3-kor-based_gpt2_review_SR5)

## Overview

Language model: [gpt3-kor-small_based_on_gpt2](https://huggingface.co/kykim/gpt3-kor-small_based_on_gpt2)

Language: Korean

Training data: review_body dataset with a star of 5 in the [naver shopping reivew dataset](https://github.com/bab2min/corpus/tree/master/sentiment).

Code: See [Ainize Workspace](https://ainize.ai/workspace/create?imageId=hnj95592adzr02xPTqss&git=https://github.com/ehdwns1516/gpt2_review_fine-tunning_note)

## Usage
## In Transformers

```
from transformers import AutoTokenizer, AutoModelWithLMHead
  
tokenizer = AutoTokenizer.from_pretrained("ehdwns1516/gpt3-kor-based_gpt2_review_SR5")

model = AutoModelWithLMHead.from_pretrained("ehdwns1516/gpt3-kor-based_gpt2_review_SR5")

generator = pipeline(
    "text-generation",
    model="ehdwns1516/gpt3-kor-based_gpt2_review_SR5",
    tokenizer=tokenizer
)

context = "your context"

result = dict()
result[0] = generator(context)[0]
```
