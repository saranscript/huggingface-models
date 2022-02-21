Hugging Face's logo
---
language: 
- en
- zu
datasets:
- JW300 + [LAFAND](https://github.com/masakhane-io/lafand-mt)
---
# m2m100_418M-zu-en-mt
## Model description
**m2m100_418M-zu-en-mt** is a **machine translation** model from isiZulu to English based on a fine-tuned facebook/m2m100_418M model.  It establishes a **baseline** for automatically translating texts from isiZulu to English.  


#### Limitations and bias
This model is limited by its training dataset. This may not generalize well for all use cases in different domains.  

## Training data
Specifically, this model is a *m2m100_418M* model that was fine-tuned on JW300 isiZulu corpus and [LAFAND](https://github.com/masakhane-io/lafand-mt). 

## Training procedure
This model was trained on NVIDIA V100 GPU

## Eval results on Test set (BLEU score)
Fine-tuning m2m100_418M achieves **29.74 BLEU** on [LAFAND test set](https://github.com/masakhane-io/lafand-mt)

### BibTeX entry and citation info
By David Adelani
```

```


