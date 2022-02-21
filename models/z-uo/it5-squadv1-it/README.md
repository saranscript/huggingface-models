---
tags:
- text2text_generation
- question_answering
language:
- it
model-index:
- name: it5-squadv1-it
  results: []
datasets:
- z-uo/squad-it
---

# Question and Answer with Italian T5

This model is a fine-tuned version of [gsarti/it5-base](https://huggingface.co/gsarti/it5-base) on [Thoroughly Cleaned Italian mC4 Corpus](https://huggingface.co/datasets/gsarti/clean_mc4_it) (~41B words, ~275GB).

To use add a question + context in the same string for example:
```
In quale anno si è verificato il terremoto nel Sichuan?
Il terremoto del Sichuan del 2008 o il terremoto del Gran Sichuan, misurato a 8.0 Ms e 7.9 Mw, e si è verificato alle 02:28:01 PM China Standard Time all' epicentro (06:28:01 UTC) il 12 maggio nella provincia del Sichuan, ha ucciso 69.197 persone e lasciato 18.222 dispersi.
```

The train achieves the following results/params:
 - epoch: 2.0
 - train_loss: 0.1064
 - train_samples: 87599
 - eval_samples : 10570
 - eval_gen_len : 9.2974
 - eval_loss : 0.5939
 - eval_rouge1 : 17.5052
 - eval_rouge2 : 5.8714
 - eval_rougeL : 17.4487
 - eval_rougeLsum : 17.4528
 
# Train the model
To train the model use [this repo](https://gitlab.com/nicolalandro/qandatrain), inside you find the requirements.txt and the src to create train.
