---
language: sw
widget:
- text: "Si kila mwenye makucha <mask> simba."
datasets:
- flax-community/swahili-safi
---

## RoBERTa in Swahili

This model was trained using HuggingFace's Flax framework and is part of the [JAX/Flax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organized by [HuggingFace](https://huggingface.co). All training was done on a TPUv3-8 VM sponsored by the Google Cloud team.

## How to use

```python
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("flax-community/roberta-swahili")

model = AutoModelForMaskedLM.from_pretrained("flax-community/roberta-swahili")

print(round((model.num_parameters())/(1000*1000)),"Million Parameters")

105 Million Parameters
```

#### **Training Data**:
This model was trained on [Swahili Safi](https://huggingface.co/datasets/flax-community/swahili-safi)

#### **Results**:
[MasakhaNER](https://github.com/masakhane-io/masakhane-ner) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1OIurb4J91X7461NQXLCCGzjeEGJq_Tyl?usp=sharing)


```
Eval metrics: {'f1': 86%}
```
This [model](https://huggingface.co/flax-community/roberta-swahili-news-classification) was fine-tuned based off this model for the
[Zindi News Classification Challenge](https://zindi.africa/hackathons/ai4d-swahili-news-classification-challenge)


#### **More Details**:
For more details and Demo please check [HF Swahili Space](https://huggingface.co/spaces/flax-community/Swahili)
