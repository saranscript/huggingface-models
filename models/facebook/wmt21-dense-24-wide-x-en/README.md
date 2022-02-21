---
language: multilingual
license: mit
tags:
- translation
- wmt21
---
# WMT 21 X-En
WMT 21 X-En is a 4.7B multilingual encoder-decoder (seq-to-seq) model trained for one-to-many multilingual translation.
It was introduced in this [paper](https://arxiv.org/abs/2108.03265) and first released in [this](https://github.com/pytorch/fairseq/tree/main/examples/wmt21) repository.

The model can directly translate text from 7 languages: Hausa (ha), Icelandic (is), Japanese (ja), Czech (cs), Russian (ru), Chinese (zh), German (de) to English. 

To translate into a target language, the target language id is forced as the first generated token.
To force the target language id as the first generated token, pass the `forced_bos_token_id` parameter to the `generate` method.

*Note: `M2M100Tokenizer` depends on `sentencepiece`, so make sure to install it before running the example.*
To install `sentencepiece` run `pip install sentencepiece`

Since the model was trained with domain tags, you should prepend them to the input as well.
* "wmtdata newsdomain": Use for sentences in the news domain
* "wmtdata otherdomain": Use for sentences in all other domain

```python
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer

model = AutoModelForSeq2SeqLM.from_pretrained("facebook/wmt21-dense-24-wide-x-en")
tokenizer = AutoTokenizer.from_pretrained("facebook/wmt21-dense-24-wide-x-en")

# translate German to English
tokenizer.src_lang = "de"
inputs = tokenizer("wmtdata newsdomain Ein Modell für viele Sprachen", return_tensors="pt")
generated_tokens = model.generate(**inputs)
tokenizer.batch_decode(generated_tokens, skip_special_tokens=True)
# => "A model for many languages"

# translate Icelandic to English
tokenizer.src_lang = "is"
inputs = tokenizer("wmtdata newsdomain Ein fyrirmynd fyrir mörg tungumál", return_tensors="pt")
generated_tokens = model.generate(**inputs)
tokenizer.batch_decode(generated_tokens, skip_special_tokens=True)
# => "One model for many languages"
```

See the [model hub](https://huggingface.co/models?filter=wmt21) to look for more fine-tuned versions.


## Languages covered
English (en), Hausa (ha), Icelandic (is), Japanese (ja), Czech (cs), Russian (ru), Chinese (zh), German (de)


## BibTeX entry and citation info
```
@inproceedings{tran2021facebook
  title={Facebook AI’s WMT21 News Translation Task Submission},
  author={Chau Tran and Shruti Bhosale and James Cross and Philipp Koehn and Sergey Edunov and Angela Fan},
  booktitle={Proc. of WMT},
  year={2021},
}
```