### SpaceRoBERTa

This is one of the 3 further pre-trained models from the SpaceTransformers family presented in [SpaceTransformers: Language Modeling for Space Systems](https://ieeexplore.ieee.org/document/9548078). The original Git repo is [strath-ace/smart-nlp](https://github.com/strath-ace/smart-nlp).

The further pre-training corpus includes publications abstracts, books, and Wikipedia pages related to space systems. Corpus size is 14.3 GB. SpaceRoBERTa was further pre-trained on this domain-specific corpus from [RoBERTa-Base](https://huggingface.co/roberta-base). In our paper, it is then fine-tuned for a Concept Recognition task.

### BibTeX entry and citation info

```
@ARTICLE{
9548078,  
author={Berquand, Audrey and Darm, Paul and Riccardi, Annalisa},  
journal={IEEE Access},   
title={SpaceTransformers: Language Modeling for Space Systems},   
year={2021},  
volume={9},  
number={},  
pages={133111-133122},  
doi={10.1109/ACCESS.2021.3115659}
}
```