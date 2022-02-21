---
language: es
---

# es-seq2seq-gender (decoder)

This is a seq2seq model (decoder half) to "flip" gender in Spanish sentences.
The model can augment your existing Spanish data, or generate counterfactuals
to test a model's decisions (would changing the gender of the subject or speaker change output?).

Intended Examples:

- el profesor viejo => la profesora vieja (article, noun, adjective all flip)
- una actriz => un actor (irregular noun)
- el lingüista => la lingüista (irregular noun)
- la biblioteca => la biblioteca (no person, no flip)

People's names are unchanged in this version, but you can use packages
such as https://pypi.org/project/gender-guesser/

## Sample code

https://colab.research.google.com/drive/1Ta_YkXx93FyxqEu_zJ-W23PjPumMNHe5

```
import torch
from transformers import AutoTokenizer, EncoderDecoderModel

model = EncoderDecoderModel.from_encoder_decoder_pretrained("monsoon-nlp/es-seq2seq-gender-encoder", "monsoon-nlp/es-seq2seq-gender-decoder")
tokenizer = AutoTokenizer.from_pretrained('monsoon-nlp/es-seq2seq-gender-decoder') # all are same as BETO uncased original

input_ids = torch.tensor(tokenizer.encode("la profesora vieja")).unsqueeze(0)
generated = model.generate(input_ids, decoder_start_token_id=model.config.decoder.pad_token_id)
tokenizer.decode(generated.tolist()[0])
> '[PAD] el profesor viejo profesor viejo profesor...'
```

## Training

I originally developed 
<a href="https://github.com/MonsoonNLP/el-la">a gender flip Python script</a>
with 
<a href="https://huggingface.co/dccuchile/bert-base-spanish-wwm-uncased">BETO</a>,
the Spanish-language BERT from Universidad de Chile,
and spaCy to parse dependencies in sentences.

More about this project: https://medium.com/ai-in-plain-english/gender-bias-in-spanish-bert-1f4d76780617

The seq2seq model is trained on gender-flipped text from that script run on the
<a href="https://huggingface.co/datasets/muchocine">muchocine dataset</a>, 
and the first 6,853 lines from the
<a href="https://oscar-corpus.com/">OSCAR corpus</a>
(Spanish ded-duped).

The encoder and decoder started with weights and vocabulary from BETO (uncased).

## Non-binary gender

This model is useful to generate male and female text samples, but falls
short of capturing gender diversity in the world and in the Spanish
language. Some communities prefer the plural -@s to represent
-os and -as, or -e and -es for gender-neutral or mixed-gender plural,
or use fewer gendered professional nouns (la juez and not jueza). This is not yet
embraced by the Royal Spanish Academy 
and is not represented in the corpora and tokenizers used to build this project.

This seq2seq project and script could, in the future, help generate more text samples 
and prepare NLP models to understand us all better.

#### Sources

- https://www.nytimes.com/2020/04/15/world/americas/argentina-gender-language.html
- https://www.washingtonpost.com/dc-md-va/2019/12/05/teens-argentina-are-leading-charge-gender-neutral-language/?arc404=true
- https://www.theguardian.com/world/2020/jan/19/gender-neutral-language-battle-spain
- https://es.wikipedia.org/wiki/Lenguaje_no_sexista
- https://remezcla.com/culture/argentine-company-re-imagines-little-prince-gender-neutral-language/
