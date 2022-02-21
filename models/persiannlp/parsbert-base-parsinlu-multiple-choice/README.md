---
language:
- fa
- multilingual
thumbnail: https://upload.wikimedia.org/wikipedia/commons/a/a2/Farsi.svg
tags:
- multiple-choice
- parsbert
- persian
- farsi
pipeline_tag: text-classification
license: cc-by-nc-sa-4.0
datasets:
- parsinlu
metrics:
- accuracy
---

# Multiple-Choice Question Answering (مدل برای پاسخ به سوالات چهار جوابی)

This is a parsbert-based model for multiple-choice question answering. 
Here is an example of how you can run this model: 

```python 
from typing import List
import torch
from transformers import AutoConfig, AutoModelForMultipleChoice, AutoTokenizer

model_name = "persiannlp/parsbert-base-parsinlu-multiple-choice"
tokenizer = AutoTokenizer.from_pretrained(model_name)
config = AutoConfig.from_pretrained(model_name)
model = AutoModelForMultipleChoice.from_pretrained(model_name, config=config)


def run_model(question: str, candicates: List[str]):
    assert len(candicates) == 4, "you need four candidates"
    choices_inputs = []
    for c in candicates:
        text_a = ""  # empty context
        text_b = question + " " + c
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
    print(output)
    return output


run_model(question="وسیع ترین کشور جهان کدام است؟", candicates=["آمریکا", "کانادا", "روسیه", "چین"])
run_model(question="طامع یعنی ؟", candicates=["آزمند", "خوش شانس", "محتاج", "مطمئن"])
run_model(
    question="زمینی به ۳۱ قطعه متساوی مفروض شده است و هر روز مساحت آماده شده برای احداث، دو برابر مساحت روز قبل است.اگر پس از (۵ روز) تمام زمین آماده شده باشد، در چه روزی یک قطعه زمین آماده شده ",
    candicates=["روز اول", "روز دوم", "روز سوم", "هیچکدام"])

```


For more details, visit this page: https://github.com/persiannlp/parsinlu/ 