---
language: tl
tags:
- electra
- tagalog
- filipino
license: gpl-3.0
inference: false
---

# ELECTRA Tagalog Base Uncased Generator
Tagalog ELECTRA model pretrained with a large corpus scraped from the internet. This model is part of a larger research project. We open-source the model to allow greater usage within the Filipino NLP community.

This is the generator model used to sample synthetic text and pretrain the discriminator. Only use this model for retraining and mask-filling. For the actual model for downstream tasks, please refer to the discriminator models.

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
