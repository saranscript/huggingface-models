---
language: nl
widget:
- text: "In het jaar 2030 zullen we"
- text: "Toen ik gisteren volledig in de ban was van"
- text: "Studenten en leraren van de Bogazici Universiteit in de Turkse stad Istanbul"
- text: "In Israël was een strenge lockdown"
tags:
- gpt-neo-1.3B
- gpt-neo
pipeline_tag: text-generation
datasets:
- yhavinga/mc4_nl_cleaned
---
# GPT Neo 1.3B pre-trained on cleaned Dutch mC4  🇳🇱

A GPT-Neo model trained from scratch on Dutch, with perplexity 16.0 on cleaned Dutch mC4.

## How To Use

You can use this GPT-Neo model directly with a pipeline for text generation.

```python
MODEL_DIR='yhavinga/gpt-neo-1.3B-dutch'
from transformers import pipeline, GPT2Tokenizer, GPTNeoForCausalLM
tokenizer = GPT2Tokenizer.from_pretrained(MODEL_DIR)
model = GPTNeoForCausalLM.from_pretrained(MODEL_DIR)
generator = pipeline('text-generation', model, tokenizer=tokenizer)

generated_text = generator('1 - geel. 2 - groen. 3 -', max_length=60, num_beams=4, no_repeat_ngram_size=3, repetition_penalty=2.0)
```

*"1 - geel. 2 - groen. 3 - rood. 4 - blauw. 5 - bruin. 6 - zwart. 7 - oranje. 8 - roze. 9 - paars. 10 - wit. 11 - grijs. 12 - magenta. 13 - lila. 14 - lichtgroen. 15"*

## Tokenizer

* BPE tokenizer trained from scratch for Dutch on mC4 nl cleaned with scripts from the Huggingface
  Transformers [Flax examples](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling).

## Dataset

This model was trained on the `full` configuration (33B tokens) of [cleaned Dutch mC4](https://huggingface.co/datasets/yhavinga/mc4_nl_cleaned),
which is the original mC4, except

  * Documents that contained words from a selection of the Dutch and English [List of Dirty Naught Obscene and Otherwise Bad Words](https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words) are removed
  * Sentences with less than 3 words are removed
  * Sentences with a word of more than 1000 characters are removed
  * Documents with less than 5 sentences are removed
  * Documents with "javascript", "lorum ipsum", "terms of use", "privacy policy", "cookie policy", "uses cookies",
    "use of cookies", "use cookies", "elementen ontbreken", "deze printversie" are removed.
 
## Models

TL;DR: [yhavinga/gpt2-medium-dutch](https://huggingface.co/yhavinga/gpt2-medium-dutch) is the best model.

* The models with `a`/`b` in the step-column have been trained to step `a` of a total of `b` steps.

|                                                                                   | model   | params | train seq len | ppl  | loss | batch size | epochs | steps           | optim     | lr     | duration | config    |
|-----------------------------------------------------------------------------------|---------|--------|---------------|------|------|------------|--------|-----------------|-----------|--------|----------|-----------|
| [yhavinga/gpt-neo-125M-dutch](https://huggingface.co/yhavinga/gpt-neo-125M-dutch) | gpt neo | 125M   | 512           | 20.9 | 3.04 | 128        | 1      | 190000/558608          | adafactor | 2.4e-3 | 1d 12h   | full |
| [yhavinga/gpt2-medium-dutch](https://huggingface.co/yhavinga/gpt2-medium-dutch)   | gpt2    | 345M   | 512           | 15.1 | 2.71 | 128        | 1      | 320000/520502   | adafactor | 8e-4   | 7d 2h    | full      |
| [yhavinga/gpt2-large-dutch](https://huggingface.co/yhavinga/gpt2-large-dutch)     | gpt2    | 762M   | 512           | 15.1 | 2.72 | 32         | 1      | 1100000/2082009 | adafactor | 3.3e-5 | 8d 15h   | large     |
| [yhavinga/gpt-neo-1.3B-dutch](https://huggingface.co/yhavinga/gpt-neo-1.3B-dutch) | gpt neo | 1.3B   | 512           | 16.0 | 2.77 | 16         | 1      | 960000/3049896  | adafactor | 5e-4   | 7d 11h   | full      |

## Acknowledgements

This project would not have been possible without compute generously provided by Google through the
[TPU Research Cloud](https://sites.research.google/trc/). The HuggingFace 🤗 ecosystem was also
instrumental in most, if not all, parts of the training. The following repositories where helpful in setting up the TPU-VM,
and training the models:

* [Gsarti's Pretrain and Fine-tune a T5 model with Flax on GCP](https://github.com/gsarti/t5-flax-gcp)
* [HUggingFace Flax MLM examples](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling)
* [gpt2-medium-persian](https://huggingface.co/flax-community/gpt2-medium-persian)
* [gpt2-medium-indonesian](https://huggingface.co/flax-community/gpt2-medium-persian)

Created by [Yeb Havinga](https://www.linkedin.com/in/yeb-havinga-86530825/)
