---
language:
- la
tags:
- language model
license: apache-2.0
datasets:
- Tesserae
- Phi5
- Thomas Aquinas
- Patrologia Latina
---

# Cicero-Similis

## Model description

A Latin Language Model, trained on Latin texts, and evaluated using the corpus of Cicero, as described in the paper _What Would Cicero Write? -- Examining Critical Textual Decisions with a Language Model_ by Todd Cook,
Published in Ciceroniana On Line, Vol. V, #2.

## Intended uses & limitations

#### How to use

Normalize text using JV Replacement and tokenize using CLTK to separate enclitics such as "-que", then:

```
from transformers import BertForMaskedLM, AutoTokenizer, FillMaskPipeline
tokenizer = AutoTokenizer.from_pretrained("cook/cicero-similis")
model = BertForMaskedLM.from_pretrained("cook/cicero-similis")
fill_mask = FillMaskPipeline(model=model, tokenizer=tokenizer, top_k=10_000)
# Cicero, De Re Publica, VI, 32, 2
# "animal" is found in A, Q, PhD manuscripts
# 'anima' H^1 Macr. et codd. Tusc.
results = fill_mask("inanimum est enim omne quod pulsu agitatur externo; quod autem est [MASK],")
```

#### Limitations and bias

Currently the model training data excludes modern and 19th century texts, but that weakness is the model's strength; it's not aimed to be a one-size-fits-all model.

## Training data

Trained on the corpora Phi5, Tesserae, Thomas Aquinas, and Patrologes Latina.


## Training procedure

5 epochs, masked language modeling .15, effective batch size 32


## Eval results
A novel evaluation metric is proposed in the paper _What Would Cicero Write? -- Examining Critical Textual Decisions with a Language Model_ by Todd Cook,
Published in Ciceroniana On Line, Vol. V, #2.

### BibTeX entry and citation info
TODO
_What Would Cicero Write? -- Examining Critical Textual Decisions with a Language Model_ by Todd Cook,
Published in Ciceroniana On Line, Vol. V, #2.