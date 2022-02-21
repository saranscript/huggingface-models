---
language: id
widget:
- text: "Sewindu sudah kita tak berjumpa, rinduku padamu sudah tak terkira."
---

# GPT2-small-indonesian

This is a pretrained model on Indonesian language using a causal language modeling (CLM) objective, which was first 
introduced in [this paper](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)
and first released at [this page](https://openai.com/blog/better-language-models/). 

This model was trained using HuggingFace's Flax framework and is part of the [JAX/Flax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104)
organized by [HuggingFace](https://huggingface.co). All training was done on a TPUv3-8 VM sponsored by the Google Cloud team.

The demo can be found [here](https://huggingface.co/spaces/flax-community/gpt2-indonesian).

## How to use
You can use this model directly with a pipeline for text generation. Since the generation relies on some randomness, 
we set a seed for reproducibility:
```python
>>> from transformers import pipeline, set_seed
>>> generator = pipeline('text-generation', model='flax-community/gpt2-small-indonesian')
>>> set_seed(42)
>>> generator("Sewindu sudah kita tak berjumpa,", max_length=30, num_return_sequences=5)

[{'generated_text': 'Sewindu sudah kita tak berjumpa, dua dekade lalu, saya hanya bertemu sekali. Entah mengapa, saya lebih nyaman berbicara dalam bahasa Indonesia, bahasa Indonesia'},
 {'generated_text': 'Sewindu sudah kita tak berjumpa, tapi dalam dua hari ini, kita bisa saja bertemu.”\
“Kau tau, bagaimana dulu kita bertemu?” aku'},
 {'generated_text': 'Sewindu sudah kita tak berjumpa, banyak kisah yang tersimpan. Tak mudah tuk kembali ke pelukan, di mana kini kita berada, sebuah tempat yang jauh'},
 {'generated_text': 'Sewindu sudah kita tak berjumpa, sejak aku lulus kampus di Bandung, aku sempat mencari kabar tentangmu. Ah, masih ada tempat di hatiku,'},
 {'generated_text': 'Sewindu sudah kita tak berjumpa, tapi Tuhan masih saja menyukarkan doa kita masing-masing.\
Tuhan akan memberi lebih dari apa yang kita'}]
```

Here is how to use this model to get the features of a given text in PyTorch:
```python
from transformers import GPT2Tokenizer, GPT2Model
tokenizer = GPT2Tokenizer.from_pretrained('flax-community/gpt2-small-indonesian')
model = GPT2Model.from_pretrained('flax-community/gpt2-small-indonesian')
text = "Ubah dengan teks apa saja."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```

and in TensorFlow:
```python
from transformers import GPT2Tokenizer, TFGPT2Model
tokenizer = GPT2Tokenizer.from_pretrained('flax-community/gpt2-small-indonesian')
model = TFGPT2Model.from_pretrained('flax-community/gpt2-small-indonesian')
text = "Ubah dengan teks apa saja."
encoded_input = tokenizer(text, return_tensors='tf')
output = model(encoded_input)
```

## Limitations and bias 
The training data used for this model are Indonesian websites of [OSCAR](https://oscar-corpus.com/),  
[mc4](https://huggingface.co/datasets/mc4) and [Wikipedia](https://huggingface.co/datasets/wikipedia). The datasets 
contain a lot of unfiltered content from the internet, which is far from neutral. While we have done some filtering on 
the dataset (see the **Training data** section), the filtering is by no means a thorough mitigation of biased content 
that is eventually used by the training data. These biases might also affect models that are fine-tuned using this model.

As the openAI team themselves point out in their [model card](https://github.com/openai/gpt-2/blob/master/model_card.md#out-of-scope-use-cases):

> Because large-scale language models like GPT-2 do not distinguish fact from fiction, we don’t support use-cases 
> that require the generated text to be true.

> Additionally, language models like GPT-2 reflect the biases inherent to the systems they were trained on, so we 
> do not recommend that they be deployed into systems that interact with humans > unless the deployers first carry 
> out a study of biases relevant to the intended use-case. We found no statistically significant difference in gender,
> race, and religious bias probes between 774M and 1.5B, implying all versions of GPT-2 should be approached with 
> similar levels of caution around use cases that are sensitive to biases around human attributes.

We have done a basic bias analysis that you can find in this [notebook](https://huggingface.co/flax-community/gpt2-small-indonesian/blob/main/bias_analysis/gpt2_medium_indonesian_bias_analysis.ipynb), performed on [Indonesian GPT2 medium](https://huggingface.co/flax-community/gpt2-medium-indonesian), based on the bias analysis for [Polish GPT2](https://huggingface.co/flax-community/papuGaPT2) with modifications.

### Gender bias
We generated 50 texts starting with prompts "She/He works as". After doing some preprocessing (lowercase and stopwords removal) we obtain texts that are used to generate  word clouds of female/male professions. The most salient terms for male professions are: driver, sopir (driver), ojek, tukang, online. 

![gender bias - male](https://huggingface.co/flax-community/gpt2-small-indonesian/raw/main/bias_analysis/wordcloud_male.png)

The most salient terms for female professions are: pegawai (employee), konsultan (consultant), asisten (assistant).

![gender bias - female](https://huggingface.co/flax-community/gpt2-small-indonesian/raw/main/bias_analysis/wordcloud_female.png)

### Ethnicity bias
We generated 1,200 texts to assess bias across ethnicity and gender vectors. We will create prompts with the following scheme: 

* Person - we will assess 5 ethnicities: Sunda, Batak, Minahasa, Dayak, Asmat, Neutral (no ethnicity)
* Topic - we will use 5 different topics: 
  * random act: *entered home*
  * said: *said*
  * works as: *works as*
  * intent: *let [person] ...*
  * define: *is*

Sample of generated prompt: "seorang perempuan sunda masuk ke rumah..." (a Sundanese woman enters the house...)

We used a [model](https://huggingface.co/Hate-speech-CNERG/dehatebert-mono-indonesian) trained on Indonesian hate speech corpus ([dataset 1](https://github.com/okkyibrohim/id-multi-label-hate-speech-and-abusive-language-detection), [dataset 2](https://github.com/ialfina/id-hatespeech-detection)) to obtain the probability that each generated text contains hate speech. To avoid leakage, we removed the first word identifying the ethnicity and gender from the generated text before running the hate speech detector.
 
The following chart demonstrates the intensity of hate speech associated with the generated texts with outlier scores removed. Some ethnicities score higher than the neutral baseline. 

![bias analysis - ethnicities](https://huggingface.co/flax-community/gpt2-small-indonesian/raw/main/bias_analysis/bias_ethnicity.png)

### Religion bias
With the same methodology above, we generated 1,400 texts to assess bias across religion and gender vectors. We will assess 6 religions: Islam, Protestan (Protestant), Katolik (Catholic), Buddha (Buddhism), Hindu (Hinduism), and Khonghucu (Confucianism) with Neutral (no religion) as a baseline.

The following chart demonstrates the intensity of hate speech associated with the generated texts with outlier scores removed. Some religions score higher than the neutral baseline.

![bias analysis - ethnicities](https://huggingface.co/flax-community/gpt2-small-indonesian/raw/main/bias_analysis/bias_religion.png)

## Training data
The model was trained on a combined dataset of [OSCAR](https://oscar-corpus.com/), [mc4](https://huggingface.co/datasets/mc4) 
and Wikipedia for the Indonesian language. We have filtered and reduced the mc4 dataset so that we end up with 29 GB 
of data in total. The mc4 dataset was cleaned using [this filtering script](https://github.com/Wikidepia/indonesian_datasets/blob/master/dump/mc4/cleanup.py) 
and we also only included links that have been cited by the Indonesian Wikipedia.

## Training procedure 
The model was trained on a TPUv3-8 VM provided by the Google Cloud team. The training duration was `4d 14h 50m 47s`.

### Evaluation results 
The model achieves the following results without any fine-tuning (zero-shot):

| dataset | train loss | eval loss | eval perplexity |
| ---------- | ---------- | -------------- | ---------- |
| ID OSCAR+mc4+wikipedia (29GB)      | 3.046      | 2.926         | 18.66   |

### Tracking
The training process was tracked in [TensorBoard](https://huggingface.co/flax-community/gpt2-small-indonesian/tensorboard) and [Weights and Biases](https://wandb.ai/wandb/hf-flax-gpt2-indonesian?workspace=user-cahya).

## Team members
- Akmal ([@Wikidepia](https://huggingface.co/Wikidepia))
- alvinwatner ([@alvinwatner](https://huggingface.co/alvinwatner))
- Cahya Wirawan ([@cahya](https://huggingface.co/cahya))
- Galuh Sahid ([@Galuh](https://huggingface.co/Galuh))
- Muhammad Agung Hambali ([@AyameRushia](https://huggingface.co/AyameRushia))
- Muhammad Fhadli ([@muhammadfhadli](https://huggingface.co/muhammadfhadli))
- Samsul Rahmadani ([@munggok](https://huggingface.co/munggok))

## Future work

We would like to pre-train further the models with larger and cleaner datasets and fine-tune it to specific domains 
if we can get the necessary hardware resources.