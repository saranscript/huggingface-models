Hugging Face's logo
---
language: 
- en
- zu
datasets:
- JW300 + [LAFAND](https://github.com/masakhane-io/lafand-mt)
---
# mt5-base-en-zu-mt
## Model description
**mt5-base-en-zu-mt** is a **machine translation** model from English to isiZulu based on a fine-tuned google/mt5-base model.  It establishes a **strong baseline** for automatically translating texts from English to isiZulu.  


#### Limitations and bias
This model is limited by its training dataset. This may not generalize well for all use cases in different domains.  

## Training data
Specifically, this model is a *mt5-base* model that was fine-tuned on JW300 isiZulu corpus and [LAFAND](https://github.com/masakhane-io/lafand-mt). The model was trained using isiXhosa (xh_ZA) as the language since the pre-trained model does not initially support isiZulu. Thus, you need to use the xh_ZA for language code when evaluating the model. 

## Training procedure
This model was trained on NVIDIA V100 GPU

## Eval results on Test set (BLEU score)
Fine-tuning mt5-base achieves **11.27 BLEU** on [LAFAND test set](https://github.com/masakhane-io/lafand-mt)

### BibTeX entry and citation info
By David Adelani
```

```


