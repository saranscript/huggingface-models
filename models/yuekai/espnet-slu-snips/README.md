Fine-tune snips dataset for SLU task using pretrained ASR model with hubert feature
---
language: 
  - en
  
receipe: "https://github.com/espnet/espnet/tree/master/egs2/snips/asr1"

datasets:
- snips: smart-lights-en-close-field

metrics:
- F1 score: 91.7
---