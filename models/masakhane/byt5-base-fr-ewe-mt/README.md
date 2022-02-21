Hugging Face's logo
---
language: 
- fr
- ee
datasets:
- JW300 + [LAFAND](https://github.com/masakhane-io/lafand-mt)
---
# byt5-base-fr-ewe-mt
## Model description
**byt5-base-fr-ewe-mt** is a **machine translation** model from French to Fon based on a fine-tuned google/byt5-base model.  It establishes a **strong baseline** for automatically translating texts from French to Fon.  


#### Limitations and bias
This model is limited by its training dataset. This may not generalize well for all use cases in different domains.  

## Training data
Specifically, this model is a *byt5-base* model that was fine-tuned on JW300 Fon corpus and [LAFAND](https://github.com/masakhane-io/lafand-mt). The model was trained using Swahili(sw_KE) as the language since the pre-trained model does not initially support Fon. Thus, you need to use the sw_KE for language code when evaluating the model. 

## Training procedure
This model was trained on NVIDIA V100 GPU

## Eval results on Test set (BLEU score)
Fine-tuning byt5-base achieves **7.3 BLEU** on [LAFAND test set](https://github.com/masakhane-io/lafand-mt)

### BibTeX entry and citation info
By David Adelani
```

```


