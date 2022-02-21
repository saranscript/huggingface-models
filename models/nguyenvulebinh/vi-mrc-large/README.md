---
language: 
- vi
- vn
- en
tags:
- question-answering
- pytorch
datasets:
- squad
license: cc-by-nc-4.0
pipeline_tag: question-answering 
metrics:
- squad
widget:
- text: "Bình là chuyên gia về gì ?"
  context: "Bình Nguyễn là một người đam mê với lĩnh vực xử lý ngôn ngữ tự nhiên . Anh nhận chứng chỉ Google Developer Expert năm 2020"
- text: "Bình được công nhận với danh hiệu gì ?"
  context: "Bình Nguyễn là một người đam mê với lĩnh vực xử lý ngôn ngữ tự nhiên . Anh nhận chứng chỉ Google Developer Expert năm 2020"
---
## Model Description

- Language model: [XLM-RoBERTa](https://huggingface.co/transformers/model_doc/xlmroberta.html)
- Fine-tune: [MRCQuestionAnswering](https://github.com/nguyenvulebinh/extractive-qa-mrc)
- Language: Vietnamese, Englsih
- Downstream-task: Extractive QA
- Dataset (combine English and Vietnamese):
  - [Squad 2.0](https://rajpurkar.github.io/SQuAD-explorer/) 
  - [mailong25](https://github.com/mailong25/bert-vietnamese-question-answering/tree/master/dataset)
  - [VLSP MRC 2021](https://vlsp.org.vn/vlsp2021/eval/mrc)
  - [MultiLingual Question Answering](https://github.com/facebookresearch/MLQA)
  
This model is intended to be used for QA in the Vietnamese language so the valid set is Vietnamese only (but English works fine). The evaluation result below uses the VLSP MRC 2021 test set. This experiment achieves TOP 1 on the leaderboard.


| Model  | EM | F1 |
| ------------- | ------------- | ------------- |
| [large](https://huggingface.co/nguyenvulebinh/vi-mrc-large)  public_test_set  | 85.847  | 83.826  |
| [large](https://huggingface.co/nguyenvulebinh/vi-mrc-large)  private_test_set  | 82.072  | 78.071  |

Public leaderboard             |  Private leaderboard
:-------------------------:|:-------------------------:
![](https://i.ibb.co/tJX6V6T/public-leaderboard.jpg)  |  ![](https://i.ibb.co/nmsX2pG/private-leaderboard.jpg)

[MRCQuestionAnswering](https://github.com/nguyenvulebinh/extractive-qa-mrc) using [XLM-RoBERTa](https://huggingface.co/transformers/model_doc/xlmroberta.html) as a pre-trained language model. By default, XLM-RoBERTa will split word in to sub-words. But in my implementation, I re-combine sub-words representation (after encoded by BERT layer) into word representation using sum strategy.

## Using pre-trained model

- Hugging Face pipeline style (**NOT using sum features strategy**).

```python
from transformers import pipeline
# model_checkpoint = "nguyenvulebinh/vi-mrc-large"
model_checkpoint = "nguyenvulebinh/vi-mrc-base"
nlp = pipeline('question-answering', model=model_checkpoint,
                   tokenizer=model_checkpoint)
QA_input = {
  'question': "Bình là chuyên gia về gì ?",
  'context': "Bình Nguyễn là một người đam mê với lĩnh vực xử lý ngôn ngữ tự nhiên . Anh nhận chứng chỉ Google Developer Expert năm 2020"
}
res = nlp(QA_input)
print('pipeline: {}'.format(res))
#{'score': 0.5782045125961304, 'start': 45, 'end': 68, 'answer': 'xử lý ngôn ngữ tự nhiên'}
```

- More accurate infer process ([**Using sum features strategy**](https://github.com/nguyenvulebinh/extractive-qa-mrc))

```python
from infer import tokenize_function, data_collator, extract_answer
from model.mrc_model import MRCQuestionAnswering
from transformers import AutoTokenizer

# model_checkpoint = "nguyenvulebinh/vi-mrc-large"
model_checkpoint = "nguyenvulebinh/vi-mrc-base"
tokenizer = AutoTokenizer.from_pretrained(model_checkpoint)
model = MRCQuestionAnswering.from_pretrained(model_checkpoint)

QA_input = {
  'question': "Bình được công nhận với danh hiệu gì ?",
  'context': "Bình Nguyễn là một người đam mê với lĩnh vực xử lý ngôn ngữ tự nhiên . Anh nhận chứng chỉ Google Developer Expert năm 2020"
}

inputs = [tokenize_function(*QA_input)]
inputs_ids = data_collator(inputs)
outputs = model(**inputs_ids)
answer = extract_answer(inputs, outputs, tokenizer)

print(answer)
# answer: Google Developer Expert. Score start: 0.9926977753639221, Score end: 0.9909810423851013
```

## About

*Built by Binh Nguyen*
[![Follow](https://img.shields.io/twitter/follow/nguyenvulebinh?style=social)](https://twitter.com/intent/follow?screen_name=nguyenvulebinh)
For more details, visit the project repository.
[![GitHub stars](https://img.shields.io/github/stars/nguyenvulebinh/extractive-qa-mrc?style=social)](https://github.com/nguyenvulebinh/extractive-qa-mrc)