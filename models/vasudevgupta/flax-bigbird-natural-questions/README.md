---
language: en
license: apache-2.0
datasets: natural_questions
widget:
- text: "Who added BigBird to HuggingFace Transformers?"
  context: "BigBird Pegasus just landed! Thanks to Vasudev Gupta, BigBird Pegasus from Google AI is merged into HuggingFace Transformers. Check it out today!!!"
---

This checkpoint is obtained after training `FlaxBigBirdForQuestionAnswering` (with extra pooler head) on [`natural_questions`](https://huggingface.co/datasets/natural_questions) dataset on TPU v3-8. This dataset takes around ~100 GB on disk. But thanks to Cloud TPUs and Jax, each epoch took just 4.5 hours. Script for training can be found here: https://github.com/vasudevgupta7/bigbird

**Use this model just like any other model from 🤗Transformers**

```python
from transformers import FlaxBigBirdForQuestionAnswering, BigBirdTokenizerFast

model_id = "vasudevgupta/flax-bigbird-natural-questions"
model = BigBirdForQuestionAnswering.from_pretrained(model_id)
tokenizer = BigBirdTokenizerFast.from_pretrained(model_id)
```

In case you are interested in predicting category (null, long, short, yes, no) as well, use `FlaxBigBirdForNaturalQuestions` (instead of `FlaxBigBirdForQuestionAnswering`) from my training script.

| Exact Match | 55.12 |
|-------------|-------|

Evaluation script: https://colab.research.google.com/github/vasudevgupta7/bigbird/blob/main/notebooks/evaluate-flax-natural-questions.ipynb