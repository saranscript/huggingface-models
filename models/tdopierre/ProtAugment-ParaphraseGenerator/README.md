---
language: "en"
tags:
- Paraphase Generation
- Data Augmentation
datasets:
- Quora
- MSR
- Google-PAWS
---

[![acl](http://img.shields.io/badge/ACL-2021-f31f32)](https://arxiv.org/abs/2105.12995)

This model is used to generate paraphrases. It has been trained on a mix of 3 different paraphrase detection datasets: MSR, Quora, Google-PAWS.

We use this model in our ACL'21 Paper ["PROTAUGMENT: Unsupervised diverse short-texts paraphrasing for intent detection meta-learning"](https://arxiv.org/abs/2105.12995)

Jointly used with generation constraints, this model allows to generate diverse paraphrases. We use those paraphrases as a data augmentation technique to further boosts a classification model's generalization capability. Feel free to play with the [code](https://github.com/tdopierre/ProtAugment)!

If you use this model, please consider citing our paper.
```
@article{Dopierre2021ProtAugmentUD,
    title={ProtAugment: Unsupervised diverse short-texts paraphrasing for intent detection meta-learning},
    author={Thomas Dopierre and C. Gravier and Wilfried Logerais},
    journal={ArXiv},
    year={2021},
    volume={abs/2105.12995}
}
```
