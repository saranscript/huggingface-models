---
datasets: pib
widget:
- text: "नमस्ते! मैं वासुदेव गुप्ता हूं"

---

mBART (a pre-trained model by Facebook) is pre-trained to de-noise multiple languages simultaneously with BART objective.

Checkpoint available in this repository is obtained after fine-tuning `facebook/mbart-large-cc25` on all samples (~260K) from Bhasha (pib_v1.3) Hindi-English parallel corpus. This checkpoint gives decent results for Hindi-english translation.