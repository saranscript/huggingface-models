---
language: sw
widget:
- text: "Si kila mwenye makucha [MASK] simba."
datasets:
- flax-community/swahili-safi
---

## BERT base-uncased for in Swahili

This model was trained using HuggingFace's Flax framework and is part of the [JAX/Flax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organized by [HuggingFace](https://huggingface.co). All training was done on a TPUv3-8 VM sponsored by the Google Cloud team.

## How to use

```python
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("flax-community/bert-base-uncased-swahili")

model = AutoModelForMaskedLM.from_pretrained("flax-community/bert-base-uncased-swahili")

print(round((model.num_parameters())/(1000*1000)),"Million Parameters")

110 Million Parameters
```

#### **Training Data**:
This model was trained on [Swahili Safi](https://huggingface.co/datasets/flax-community/swahili-safi)


#### **More Details**:
For more details and Demo please check [HF Swahili Space](https://huggingface.co/spaces/flax-community/Swahili)
