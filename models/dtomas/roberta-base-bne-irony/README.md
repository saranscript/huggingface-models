---
language: 
  - es
tags:
  - irony
  - sarcasm
  - spanish
widget:
- text: "¡Cómo disfruto peleándome con los Transformers!"
  example_title: "Ironic"
- text: "Madrid es la capital de España"
  example_title: "Non ironic"
  
---

# RoBERTa base finetuned for Spanish irony detection

## Model description

Model to perform irony detection in Spanish. This is a finetuned version of the [RoBERTa-base-bne model](https://huggingface.co/PlanTL-GOB-ES/roberta-base-bne) on the [IroSvA](https://www.autoritas.net/IroSvA2019/) corpus. Only the Spanish from Spain variant was used in the training process. It comprises 2,400 tweets labeled as ironic/non-ironic.


