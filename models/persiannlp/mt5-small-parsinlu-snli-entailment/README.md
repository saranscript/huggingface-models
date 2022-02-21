---
language:
- fa
- multilingual
thumbnail: https://upload.wikimedia.org/wikipedia/commons/a/a2/Farsi.svg
tags:
- entailment
- mt5
- persian
- farsi
license: cc-by-nc-sa-4.0
datasets:
- parsinlu
- snli
metrics:
- accuracy
---

# Textual Entailment (مدل برای پاسخ به استلزام منطقی)

This is a model for textual entailment problems. 
Here is an example of how you can run this model: 

```python 
from transformers import MT5ForConditionalGeneration, MT5Tokenizer

model_size="small"
model_name = f"persiannlp/mt5-{model_size}-parsinlu-snli-entailment"
tokenizer = MT5Tokenizer.from_pretrained(model_name)
model = MT5ForConditionalGeneration.from_pretrained(model_name)


def run_model(premise, hypothesis, **generator_args):
    input_ids = tokenizer.encode(f"{premise}<sep>{hypothesis}", return_tensors="pt")
    res = model.generate(input_ids, **generator_args)
    output = tokenizer.batch_decode(res, skip_special_tokens=True)
    print(output)
    return output


run_model(
    "این مسابقات بین آوریل و دسامبر در هیپودروم ولیفندی در نزدیکی باکرکی ، ۱۵ کیلومتری (۹ مایل) غرب استانبول برگزار می شود.",
    "در ولیفندی هیپودروم، مسابقاتی از آوریل تا دسامبر وجود دارد."
)

run_model(
"آیا کودکانی وجود دارند که نیاز به سرگرمی دارند؟",
    "هیچ کودکی هرگز نمی خواهد سرگرم شود.",
)

run_model(
    "ما به سفرهایی رفته ایم که در نهرهایی شنا کرده ایم",
    "علاوه بر استحمام در نهرها ، ما به اسپا ها و سونا ها نیز رفته ایم."
)
```


For more details, visit this page: https://github.com/persiannlp/parsinlu/ 
