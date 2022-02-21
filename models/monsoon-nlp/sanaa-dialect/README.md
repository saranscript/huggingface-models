---
language: ar
---

# Sanaa-Dialect
## Finetuned Arabic GPT-2 demo

This is a small GPT-2 model, originally trained on Arabic Wikipedia circa September 2020 ,
finetuned on dialect datasets from Qatar University, University of British Columbia / NLP,
and Johns Hopkins University / LREC

- https://qspace.qu.edu.qa/handle/10576/15265
- https://github.com/UBC-NLP/aoc_id
- https://github.com/ryancotterell/arabic_dialect_annotation

You can use special tokens to prompt five dialects: `[EGYPTIAN]`, `[GULF]`, `[LEVANTINE]`, `[MAGHREBI]`, and `[MSA]`

```
from simpletransformers.language_generation import LanguageGenerationModel
model = LanguageGenerationModel("gpt2", "monsoon-nlp/sanaa-dialect")
model.generate('[GULF]' + "مدينتي هي", { 'max_length': 100 })
```

There is NO content filtering in the current version; do not use for public-facing
text generation!

## Training and Finetuning details

Original model and training: https://huggingface.co/monsoon-nlp/sanaa

I inserted new tokens into the tokenizer, finetuned the model on the dialect samples, and exported the new model.

Notebook: https://colab.research.google.com/drive/1fXFH7g4nfbxBo42icI4ZMy-0TAGAxc2i

شكرا لتجربة هذا! ارجو التواصل معي مع الاسئلة

