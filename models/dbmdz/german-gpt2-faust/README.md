---
language: de

widget:
- text: "Schon um die Liebe"

license: mit
---

# German GPT-2 model

In this repository we release (yet another) GPT-2 model, that was trained on various texts for German.

The model is meant to be an entry point for fine-tuning on other texts, and it is definitely not as good or "dangerous" as the English GPT-3 model. We do not plan extensive PR or staged releases for this model 😉

**Note**: The model was initially released under an anonymous alias (`anonymous-german-nlp/german-gpt2`) so we now "de-anonymize" it.

More details about GPT-2 can be found in the great [Hugging Face](https://huggingface.co/transformers/model_doc/gpt2.html) documentation.

## German GPT-2 fine-tuned on Faust I and II

We fine-tuned our German GPT-2 model on "Faust I and II" from Johann Wolfgang Goethe. These texts can be obtained from [Deutsches Textarchiv (DTA)](http://www.deutschestextarchiv.de/book/show/goethe_faust01_1808). We use the "normalized" version of both texts (to avoid out-of-vocabulary problems with e.g. "ſ")

Fine-Tuning was done for 100 epochs, using a batch size of 4 with half precision on a RTX 3090. Total time was around 12 minutes (it is really fast!).

We also open source this fine-tuned model. Text can be generated with:

```python
from transformers import pipeline

pipe = pipeline('text-generation', model="dbmdz/german-gpt2-faust",
                 tokenizer="dbmdz/german-gpt2-faust")   

text = pipe("Schon um die Liebe", max_length=100)[0]["generated_text"]

print(text)
```

and could output:

```
Schon um die Liebe bitte ich, Herr! Wer mag sich die dreifach Ermächtigen?
Sei mir ein Held!
Und daß die Stunde kommt spreche ich nicht aus.
Faust (schaudernd).
Den schönen Boten finde' ich verwirrend;
```

# License

All models are licensed under [MIT](LICENSE).

# Huggingface model hub

All models are available on the [Huggingface model hub](https://huggingface.co/dbmdz).

# Contact (Bugs, Feedback, Contribution and more)

For questions about our BERT models just open an issue
[here](https://github.com/stefan-it/german-gpt/issues/new) 🤗

# Acknowledgments

Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC).
Thanks for providing access to the TFRC ❤️

Thanks to the generous support from the [Hugging Face](https://huggingface.co/) team,
it is possible to download both cased and uncased models from their S3 storage 🤗
