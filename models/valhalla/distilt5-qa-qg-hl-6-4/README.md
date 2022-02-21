---
datasets:
- squad
tags:
- question-generation
- distilt5
- distilt5-qg
widget:
- text: 'generate question: <hl> 42 <hl> is the answer to life, the universe and everything.
    </s>'
- text: 'question: What is 42 context: 42 is the answer to life, the universe and
    everything. </s>'
license: mit
---

## DistilT5 for question-generation
This is distilled version of [t5-small-qa-qg-hl](https://huggingface.co/valhalla/t5-small-qa-qg-hl) model trained for question answering and answer aware question generation tasks.

The model is distilled using the **No Teacher Distillation** method proposed by Huggingface, [here](https://github.com/huggingface/transformers/tree/master/examples/seq2seq#distilbart).

We just copy alternating layers from `t5-small-qa-qg-hl` and finetune more on the same data. Following table lists other distilled models and their metrics.

| Name                                                                            | BLEU-4  | METEOR  | ROUGE-L | QA-EM  | QA-F1  |
|---------------------------------------------------------------------------------|---------|---------|---------|--------|--------|
| [distilt5-qg-hl-6-4](https://huggingface.co/valhalla/distilt5-qg-hl-6-4)        | 18.4141 | 24.8417 | 40.3435 | -      | -      |
| [distilt5-qa-qg-hl-6-4](https://huggingface.co/valhalla/distilt5-qa-qg-hl-6-4)  | 18.6493 | 24.9685 | 40.5605 | 76.13  | 84.659 |
| [distilt5-qg-hl-12-6](https://huggingface.co/valhalla/distilt5-qg-hl-12-6)      | 20.5275 | 26.5010 | 43.2676 | -      | -      |
| [distilt5-qa-qg-hl-12-6](https://huggingface.co/valhalla/distilt5-qa-qg-hl-12-6)| 20.6109 | 26.4533 | 43.0895 | 81.61  | 89.831 |


You can play with the model using the inference API. Here's how you can use it

For QG

`generate question: <hl> 42 <hl> is the answer to life, the universe and everything.`

For QA

`question: What is 42 context: 42 is the answer to life, the universe and everything.`

For more deatils see [this](https://github.com/patil-suraj/question_generation) repo.

### Model in action 🚀

You'll need to clone the [repo](https://github.com/patil-suraj/question_generation).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/patil-suraj/question_generation/blob/master/question_generation.ipynb)


```python3
from pipelines import pipeline
nlp = pipeline("multitask-qa-qg", model="valhalla/distilt5-qa-qg-hl-6-4")

# to generate questions simply pass the text
nlp("42 is the answer to life, the universe and everything.")
=> [{'answer': '42', 'question': 'What is the answer to life?'}]

# for qa pass a dict with "question" and "context"
nlp({
    "question": "What is 42 ?",
    "context": "42 is the answer to life, the universe and everything."
})
=> 'the answer to life, the universe and everything'
```