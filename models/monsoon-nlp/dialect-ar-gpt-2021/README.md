---
language: ar
---

# Dialect-AR-GPT-2021
## Finetuned AraGPT-2 demo

This model started with [AraGPT2-Medium](https://huggingface.co/aubmindlab/aragpt2-medium),
from AUB MIND Lab.

This model was then finetuned on dialect datasets from Qatar University, University of British Columbia / NLP,
and Johns Hopkins University / LREC for 10 epochs.

You can use special tokens to prompt five dialects: `[EGYPTIAN]`, `[GULF]`, `[LEVANTINE]`, `[MAGHREBI]`, or `[MSA]`, followed by a space.

```
from simpletransformers.language_generation import LanguageGenerationModel
model = LanguageGenerationModel("gpt2", "monsoon-nlp/dialect-ar-gpt-2021")
model.generate('[GULF] ' + "Ù…Ø¯ÙŠÙ†ØªÙŠ Ù‡ÙŠ", { 'max_length': 100 })
```

There is NO content filtering in the current version; do not use for public-facing
text generation!

## Training and Finetuning details

Original model: https://huggingface.co/aubmindlab/aragpt2-medium

I inserted new tokens into the tokenizer, finetuned the model on the dialect samples, and exported the new model.

Notebook: https://colab.research.google.com/drive/19C0zbkSCt5ncVCa4kY-ik9hSEiJcjI-F

## Citations 

AraGPT2 model:

```
@misc{antoun2020aragpt2,
      title={AraGPT2: Pre-Trained Transformer for Arabic Language Generation},
      author={Wissam Antoun and Fady Baly and Hazem Hajj},
      year={2020},
      eprint={2012.15520},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

Dialect data sources:
- https://qspace.qu.edu.qa/handle/10576/15265
- https://github.com/UBC-NLP/aoc_id
- https://github.com/ryancotterell/arabic_dialect_annotation
