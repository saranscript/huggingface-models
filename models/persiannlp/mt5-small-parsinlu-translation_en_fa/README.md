---
language:
- fa
- multilingual
thumbnail: https://upload.wikimedia.org/wikipedia/commons/a/a2/Farsi.svg
tags:
- machine-translation
- mt5
- persian
- farsi
license: cc-by-nc-sa-4.0
datasets:
- parsinlu
metrics:
- sacrebleu
---

# Machine Translation (ترجمه‌ی ماشینی)

This is an mT5-based model for machine translation (English -> Persian). 
Here is an example of how you can run this model: 

```python 
from transformers import MT5ForConditionalGeneration, MT5Tokenizer

model_size = "small"
model_name = f"persiannlp/mt5-{model_size}-parsinlu-translation_en_fa"
tokenizer = MT5Tokenizer.from_pretrained(model_name)
model = MT5ForConditionalGeneration.from_pretrained(model_name)


def run_model(input_string, **generator_args):
    input_ids = tokenizer.encode(input_string, return_tensors="pt")
    res = model.generate(input_ids, **generator_args)
    output = tokenizer.batch_decode(res, skip_special_tokens=True)
    print(output)
    return output


run_model("Praise be to Allah, the Cherisher and Sustainer of the worlds;")
run_model("shrouds herself in white and walks penitentially disguised as brotherly love through factories and parliaments; offers help, but desires power;")
run_model("He thanked all fellow bloggers and organizations that showed support.")
run_model("Races are held between April and December at the Veliefendi Hippodrome near Bakerky, 15 km (9 miles) west of Istanbul.")
run_model("I want to pursue PhD in Computer Science about social network,what is the open problem in social networks?")
```
which should output: 
```
['برای الله، یعنی چرنده و سوزان دنیا، تحسین کنید']
['خودش را در سفید پوسته می کند و به صورت عشق برادرانه']
['او از تمام بلاگرها و سازمان هایی که حمایتشان را نشان می داد']
['در طول ماه آوریل و دسامبر در والی فیودورونا نزدیک بیکر']
['من می خواهم در مورد شبکه اجتماعی تحقیقات علوم کامپیوتری را دن']
```

For more details, visit this page: https://github.com/persiannlp/parsinlu/ 
