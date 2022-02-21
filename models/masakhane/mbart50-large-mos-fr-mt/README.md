Hugging Face's logo
---
language: 
- fr
- mos
datasets:
- JW300 + [LAFAND](https://github.com/masakhane-io/lafand-mt)
---
# mbart50-large-mos-fr-mt
## Model description
**mbart50-large-mos-fr-mt** is a **machine translation** model from Mossi to French based on a fine-tuned facebook/mbart-large-50 model.  It establishes a **strong baseline** for automatically translating texts from Mossi to French.  


#### Limitations and bias
This model is limited by its training dataset. This may not generalize well for all use cases in different domains.  

## Training data
Specifically, this model is a *mbart-large-50* model that was fine-tuned on JW300 Mossi corpus and [LAFAND](https://github.com/masakhane-io/lafand-mt). The model was trained using Swahili(sw_KE) as the language since the pre-trained model does not initially support Mossi. Thus, you need to use the sw_KE for language code when evaluating the model. 

## Training procedure
This model was trained on NVIDIA V100 GPU

## Eval results on Test set (BLEU score)
Fine-tuning mbart50-large achieves **6.07 BLEU** on [LAFAND test set](https://github.com/masakhane-io/lafand-mt)

### BibTeX entry and citation info
By David Adelani
```

```


