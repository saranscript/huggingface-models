---
widget:
- text: "The CubeSat RF design shall either have one RF inhibit and a RF power output no greater than 1.5W at the transmitter antenna's RF input OR the CubeSat shall have a minimum of two independent RF inhibits (CDS 3.3.9) (ISO 5.5.6)."
---

---

# spaceroberta_CR



## Model desciption

This is fine-tuned further SpaceSciBERT model from the SpaceTransformers model family presented in SpaceTransformers: Language Modeling for Space Systems. The original Git repo is strath-ace/smart-nlp. The [fine-tuning](https://github.com/strath-ace/smart-nlp/blob/master/SpaceTransformers/CR/CR_ECSS_dataset.json) dataset is available for download and consists of 874 unique manual annotated ECSS requirements. 

The notebookfor fine-tuning can be assesed in Google Colab:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1EGh9bdxq6RqIzbvKuptAWvmIBG2EQJzJ?usp=sharing)

### BibTeX entry and citation info

```
@ARTICLE{ 9548078,
author={Berquand, Audrey and Darm, Paul and Riccardi, Annalisa},
journal={IEEE Access},
title={SpaceTransformers: Language Modeling for Space Systems},
year={2021},
volume={9},
number={},
pages={133111-133122},
doi={10.1109/ACCESS.2021.3115659} }
```