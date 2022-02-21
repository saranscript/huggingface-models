Hugging Face's logo
---
language: 
- fr
- mos
datasets:
- JW300 + [LAFAND](https://github.com/masakhane-io/lafand-mt)
---
# m2m100_418M-mos-fr-mt
## Model description
**m2m100_418M-mos-fr-mt** is a **machine translation** model from Mossi to French based on a fine-tuned facebook/m2m100_418M model.  It establishes a **baseline** for automatically translating texts from Mossi to French.  


#### Limitations and bias
This model is limited by its training dataset. This may not generalize well for all use cases in different domains.  

## Training data
Specifically, this model is a *m2m100_418M* model that was fine-tuned on JW300 Mossi corpus and [LAFAND](https://github.com/masakhane-io/lafand-mt). 

## Training procedure
This model was trained on NVIDIA V100 GPU

## Eval results on Test set (BLEU score)
Fine-tuning m2m100_418M achieves **6.07 BLEU** on [LAFAND test set](https://github.com/masakhane-io/lafand-mt)

### BibTeX entry and citation info
By David Adelani
```

```


