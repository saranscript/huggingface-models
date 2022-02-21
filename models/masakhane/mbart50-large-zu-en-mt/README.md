Hugging Face's logo
---
language: 
- en
- zu
datasets:
- JW300 + [LAFAND](https://github.com/masakhane-io/lafand-mt)
---
# mbart50-large-zu-en-mt
## Model description
**mbart50-large-zu-en-mt** is a **machine translation** model from isiZulu to English based on a fine-tuned facebook/mbart-large-50 model.  It establishes a **strong baseline** for automatically translating texts from isiZulu to English.  


#### Limitations and bias
This model is limited by its training dataset. This may not generalize well for all use cases in different domains.  

## Training data
Specifically, this model is a *mbart-large-50* model that was fine-tuned on JW300 isiZulu corpus and [LAFAND](https://github.com/masakhane-io/lafand-mt). The model was trained using Xhosa(xh_ZA) as the language since the pre-trained model does not initially support isiZulu. Thus, you need to use the xh_ZA for language code when evaluating the model. 

## Training procedure
This model was trained on NVIDIA V100 GPU

## Eval results on Test set (BLEU score)
Fine-tuning mbart50-large achieves **33.56 BLEU** on [LAFAND test set](https://github.com/masakhane-io/lafand-mt)

### BibTeX entry and citation info
By David Adelani
```

```


