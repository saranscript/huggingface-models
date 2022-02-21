---
license: cc-by-sa-3.0
language: ja
tags:
- question-answering
- extractive-qa
pipeline_tag:
- None
datasets:
- SkelterLabsInc/JaQuAD
metrics:
- Exact match
- F1 score
---

# BERT base Japanese - JaQuAD

## Description

A Japanese Question Answering model fine-tuned on [JaQuAD](https://huggingface.co/datasets/SkelterLabsInc/JaQuAD).
Please refer [BERT base Japanese](https://huggingface.co/cl-tohoku/bert-base-japanese) for details about the pre-training model.
The codes for the fine-tuning are available at [SkelterLabsInc/JaQuAD](https://github.com/SkelterLabsInc/JaQuAD)

## Evaluation results

On the development set.

```shell
{"f1": 77.35, "exact_match": 61.01}
```

On the test set.

```shell
{"f1": 78.92, "exact_match": 63.38}
```

## Usage

```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer

question = 'アレクサンダー・グラハム・ベルは、どこで生まれたの?'
context = 'アレクサンダー・グラハム・ベルは、スコットランド生まれの科学者、発明家、工学者である。世界初の>実用的電話の発明で知られている。'

model = AutoModelForQuestionAnswering.from_pretrained(
    'SkelterLabsInc/bert-base-japanese-jaquad')
tokenizer = AutoTokenizer.from_pretrained(
    'SkelterLabsInc/bert-base-japanese-jaquad')

inputs = tokenizer(
    question, context, add_special_tokens=True, return_tensors="pt")
input_ids = inputs["input_ids"].tolist()[0]
outputs = model(**inputs)
answer_start_scores = outputs.start_logits
answer_end_scores = outputs.end_logits

# Get the most likely beginning of answer with the argmax of the score.
answer_start = torch.argmax(answer_start_scores)
# Get the most likely end of answer with the argmax of the score.
# 1 is added to `answer_end` because the index pointed by score is inclusive.
answer_end = torch.argmax(answer_end_scores) + 1

answer = tokenizer.convert_tokens_to_string(
    tokenizer.convert_ids_to_tokens(input_ids[answer_start:answer_end]))
# answer = 'スコットランド'
```

## License

The fine-tuned model is licensed under the [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) license.

## Citation

```bibtex
@misc{so2022jaquad,
      title={{JaQuAD: Japanese Question Answering Dataset for Machine Reading Comprehension}},
      author={ByungHoon So and Kyuhong Byun and Kyungwon Kang and Seongjin Cho},
      year={2022},
      eprint={2202.01764},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```