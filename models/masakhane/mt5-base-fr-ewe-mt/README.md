Hugging Face's logo
---
language: 
- fr
- ee
datasets:
- JW300 + [LAFAND](https://github.com/masakhane-io/lafand-mt)
---
# mt5-base-fr-ewe-mt
## Model description
**mt5-base-fr-ewe-mt** is a **machine translation** model from French to Ewe based on a fine-tuned google/mt5-base model.  It establishes a **strong baseline** for automatically translating texts from French to Ewe.  


#### Limitations and bias
This model is limited by its training dataset. This may not generalize well for all use cases in different domains.  

## Training data
Specifically, this model is a *mt5-base* model that was fine-tuned on JW300 Ewe corpus and [LAFAND](https://github.com/masakhane-io/lafand-mt). The model was trained using Swahili(sw_KE) as the language since the pre-trained model does not initially support Ewe. Thus, you need to use the sw_KE for language code when evaluating the model. 

## Training procedure
This model was trained on NVIDIA V100 GPU

## Eval results on Test set (BLEU score)
Fine-tuning mt5-base achieves **6.27 BLEU** on [LAFAND test set](https://github.com/masakhane-io/lafand-mt)

### BibTeX entry and citation info
By David Adelani
```

```


