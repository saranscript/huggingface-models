---
language: de
widget:
- text: "Heute ist sehr schönes Wetter in"
license: mit
---

# German GPT-2 model
In this repository we release (yet another) GPT-2 model, that was trained on ~90 GB from the ["German colossal, clean Common Crawl corpus"](https://german-nlp-group.github.io/projects/gc4-corpus.html) (GC4).

The model is meant to be an entry point for fine-tuning on other texts, and it is definitely not as good or "dangerous" as the English GPT-3 model. We do not plan extensive PR or staged releases for this model 😉

---

**Disclaimer**: the presented and trained language models in this repository are for **research only** purposes.
The GC4 corpus - that was used for training - contains crawled texts from the internet. Thus, this GPT-2 model can
be considered as highly biased, resulting in a model that encodes stereotypical associations along gender, race,
ethnicity and disability status. Before using and working with the released checkpoints, it is highly recommended
to read:

[On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?](https://faculty.washington.edu/ebender/papers/Stochastic_Parrots.pdf)

from Emily M. Bender, Timnit Gebru, Angelina McMillan-Major and Shmargaret Shmitchell.

The aim of this released GPT-2 model for German is to boost research on (large) pre-trained language models for German, especially
for identifying biases and how to prevent them, as most research is currently done for English only.

---

# Changelog

* 17.10.2021: We highly recommend to try the Text Generation Pipeline in Transformers. The quality of the generated text from the Inference Widget here can be lower.
* 06.09.2021: Initial release. Detailed information about training parameters coming soon.

# Text Generation

The following code snippet can be used to generate text with this German GPT-2 model:

```python
from transformers import pipeline

model_name = "stefan-it/german-gpt2-larger"

pipe = pipeline('text-generation', model=model_name, tokenizer=model_name)

text = pipe("Der Sinn des Lebens ist es", max_length=200)[0]["generated_text"]

print(text)
```

# Training Data

The following archives are used for training the (first version) of this GPT-2 model:

* `de_head_0000_2015-48.tar.gz`
* `de_head_0000_2016-18.tar.gz`
* `de_head_0000_2016-44.tar.gz`
* `de_head_0000_2017-13.tar.gz`
* `de_head_0000_2017-30.tar.gz`
* `de_head_0000_2017-39.tar.gz`
* `de_head_0000_2017-51.tar.gz`
* `de_head_0000_2018-09.tar.gz`
* `de_head_0000_2018-17.tar.gz`
* `de_head_0000_2018-30.tar.gz`
* `de_head_0000_2018-39.tar.gz`
* `de_head_0000_2018-51.tar.gz`
* `de_head_0000_2019-18.tar.gz`
* `de_head_0000_2019-30.tar.gz`
* `de_head_0006_2019-09.tar.gz`
* `de_head_0006_2019-18.tar.gz`
* `de_head_0006_2019-30.tar.gz`
* `de_head_0006_2019-47.tar.gz`
* `de_head_0006_2020-10.tar.gz`
* `de_head_0007_2018-30.tar.gz`
* `de_head_0007_2018-51.tar.gz`
* `de_head_0007_2019-09.tar.gz`
* `de_head_0007_2019-18.tar.gz`
* `de_head_0007_2019-47.tar.gz`
* `de_head_0007_2020-10.tar.gz`

Details and URLs can be found on the [GC4](https://german-nlp-group.github.io/projects/gc4-corpus.html)
page.

Archives are then extracted and NLTK (`german` model) is used to sentence split the corpus.
This results in a total training corpus size of 90GB.

# Training Details

We use the recently re-trained `dbmdz/german-gpt2` ([version 2](https://huggingface.co/dbmdz/german-gpt2)!)
model as back-bone model. Thus, the tokenizer and vocab is the same as used in the `dbmdz/german-gpt2` model.

The model was trained on a v3-8 TPU, with the following parameters:

```bash
python ./run_clm_flax.py --output_dir=/mnt/datasets/german-gpt2-larger/ --name_or_path dbmdz/german-gpt2 --do_train --do_eval --block_size=512 --per_device_train_batch_size=16 --per_device_eval_batch_size=16 --learning_rate=5e-3 --warmup_steps=1000 --adam_beta1=0.9 --adam_beta2=0.98 --weight_decay=0.01 --overwrite_output_dir --num_train_epochs=20 --logging_steps=500 --save_steps=2500 --eval_steps=2500 --train_file /mnt/datasets/gc4/train.txt --validation_file /mnt/datasets/gc4/validation.txt --preprocessing_num_workers 16
```

Training took around 17 days for 20 epochs.

# Acknowledgments
Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC).
Thanks for providing access to the TFRC ❤️

Thanks to the generous support from the [Hugging Face](https://huggingface.co/) team,
it is possible to download this model from their S3 storage 🤗

This project heavily profited from the amazing Hugging Face
[Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104).
Many thanks for the great organization and discussions during and after the week!