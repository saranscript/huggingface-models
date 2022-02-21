---
language:
- mk
thumbnail: https://huggingface.co/macedonizer/blaze-koneski/blaze-koneski.jpg
license: apache-2.0
datasets:
- wiki-mk
- blaze-koneski-poetry
---

# blaze-koneski
GPT-2 type of model. We finetuned macedonizer/mk-gpt-2 with Blaze Koneski's poetry.

## About Blaze Koneski
Born in a village near Prilep in 1921. Studied philology at Skopje University and worked there as a professor. Was the first chairman of the Macedonian Academy of Sciences and Arts, corresponding member of the Yugoslav Academy of Sciences and Arts, as well as of the Serbian and Slovene Academies, and honorary doctor of the Universities of Chicago and Krakow.

Wrote poetry, short stories, and essays, as well as scholarly works, many of them on the Macedonian language. Editor of the Dictionarv of the Macedonian Language, translator of Heine and Shakespeare. His works have been translated into Serbian, Croatian, Slovene, Albanian, Turkish, Hungarian, French, Russian, Italian, Greek, Polish, Romanian, German, and English.

Winner of numerous prizes, including the Golden Wreath of the Struga Poetry Evenings.

### How to use
Here is how to use this model to get the features of a given text in PyTorch:

import random
from transformers import AutoTokenizer, AutoModelWithLMHead

tokenizer = AutoTokenizer.from_pretrained('macedonizer/blaze-koneski')
nmodel = AutoModelWithLMHead.from_pretrained('macedonizer/blaze-koneski')

input_text = 'Москва '

if len(input_text) == 0: \
    encoded_input = tokenizer(input_text, return_tensors="pt") \
    output = model.generate( \
        bos_token_id=random.randint(1, 50000), \
        do_sample=True, \
        top_k=50, \
        max_length=1024, \
        top_p=0.95, \
        num_return_sequences=1, \
     ) \
else: \
    encoded_input = tokenizer(input_text, return_tensors="pt") \
    output = model.generate( \
        **encoded_input, \
        bos_token_id=random.randint(1, 50000), \
        do_sample=True, \
        top_k=50, \
        max_length=1024, \
        top_p=0.95, \
        num_return_sequences=1, \
    )

decoded_output = [] \
for sample in output: \
    decoded_output.append(tokenizer.decode(sample, skip_special_tokens=True))

print(decoded_output)