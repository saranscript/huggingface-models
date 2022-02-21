---
language:
- fa
- multilingual
thumbnail: https://upload.wikimedia.org/wikipedia/commons/a/a2/Farsi.svg
tags:
- query-paraphrasing
- mt5
- persian
- farsi
license: cc-by-nc-sa-4.0
datasets:
- parsinlu
- qqp
metrics:
- accuracy
---

# Detection of Paraphrased Queries (تشخصیص سوالات هم‌معنی)

This is a model for detection of paraphrased queries. 
Here is an example of how you can run this model: 

```python 
from transformers import MT5Config, MT5ForConditionalGeneration, MT5Tokenizer

model_name = "persiannlp/mt5-large-parsinlu-qqp-query-paraphrasing"
tokenizer = MT5Tokenizer.from_pretrained(model_name)
model = MT5ForConditionalGeneration.from_pretrained(model_name)

def run_model(q1, q2, **generator_args):
    input_ids = tokenizer.encode(f"{q1}<sep>{q2}", return_tensors="pt")
    res = model.generate(input_ids, **generator_args)
    output = tokenizer.batch_decode(res, skip_special_tokens=True)
    print(output)
    return output


run_model("چه چیزی باعث پوکی استخوان می شود؟", "چه چیزی باعث مقاومت استخوان در برابر ضربه می شود؟")
run_model("من دارم به این فکر میکنم چرا ساعت هفت نمیشه؟", "چرا من ساده فکر میکردم به عشقت پابندی؟")
run_model("دعای کمیل در چه روزهایی خوانده می شود؟", "دعای جوشن کبیر در چه شبی خوانده می شود؟")
run_model("دعای کمیل در چه روزهایی خوانده می شود؟", "دعای جوشن کبیر در چه شبی خوانده می شود؟")
run_model("شناسنامه در چه سالی وارد ایران شد؟", "سیب زمینی در چه سالی وارد ایران شد؟")
run_model("سیب زمینی چه زمانی وارد ایران شد؟", "سیب زمینی در چه سالی وارد ایران شد؟")
```


For more details, visit this page: https://github.com/persiannlp/parsinlu/ 
