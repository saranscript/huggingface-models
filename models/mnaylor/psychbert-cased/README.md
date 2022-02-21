# PsychBERT
This domain adapted language model is pretrained from the `bert-base-cased` checkpoint on masked language modeling, using a dataset of ~40,000 PubMed papers in the domain of psychology, psychiatry, mental health, and behavioral health; as well as a dastaset of roughly 200,000 social media conversations about mental health. This work is submitted as an entry for BIBM 2021.

**Note**: the token-prediction widget on this page does not work with Flax models. In order to use the model, please pull it into a Python session as follows:

```
from transformers import FlaxAutoModelForMaskedLM, AutoModelForMaskedLM

# load as a flax model
flax_lm = FlaxAutoModelForMaskedLM.from_pretrained('mnaylor/psychbert-cased')

# load as a pytorch model 
# requires flax to be installed in your environment
pytorch_lm = AutoModelForMaskedLM.from_pretrained('mnaylor/psychbert-cased', from_flax=True)
```

Authors: Vedant Vajre, Mitch Naylor, Uday Kamath, Amarda Shehu