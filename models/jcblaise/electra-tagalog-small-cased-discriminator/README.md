---
language: tl
tags:
- electra
- tagalog
- filipino
license: gpl-3.0
inference: false
---

**Deprecation Notice**  
This model is deprecated. New Filipino Transformer models trained with a much larger corpora are available.  
Use [`jcblaise/roberta-tagalog-base`](https://huggingface.co/jcblaise/roberta-tagalog-base) or [`jcblaise/roberta-tagalog-large`](https://huggingface.co/jcblaise/roberta-tagalog-large) instead for better performance.

---

# ELECTRA Tagalog Small Cased Discriminator
Tagalog ELECTRA model pretrained with a large corpus scraped from the internet. This model is part of a larger research project. We open-source the model to allow greater usage within the Filipino NLP community.

This is the discriminator model, which is the main Transformer used for finetuning to downstream tasks. For generation, mask-filling, and retraining, refer to the Generator models.

## Citations
All model details and training setups can be found in our papers. If you use our model or find it useful in your projects, please cite our work:

```
@inproceedings{cruz2021exploiting,
  title={Exploiting News Article Structure for Automatic Corpus Generation of Entailment Datasets},
  author={Cruz, Jan Christian Blaise and Resabal, Jose Kristian and Lin, James and Velasco, Dan John and Cheng, Charibeth},
  booktitle={Pacific Rim International Conference on Artificial Intelligence},
  pages={86--99},
  year={2021},
  organization={Springer}
}
```

## Data and Other Resources
Data used to train this model as well as other benchmark datasets in Filipino can be found in my website at https://blaisecruz.com

## Contact
If you have questions, concerns, or if you just want to chat about NLP and low-resource languages in general, you may reach me through my work email at me@blaisecruz.com
