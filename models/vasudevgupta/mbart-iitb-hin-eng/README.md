---
datasets: pib
widget:
- text: "नमस्ते! मैं वासुदेव गुप्ता हूं"

---

mBART (a pre-trained model by Facebook) is pre-trained to de-noise multiple languages simultaneously with BART objective.

Checkpoint available in this repository is obtained after fine-tuning `facebook/mbart-large-cc25` on 0.5 M samples from IIT-B Hindi-English parallel corpus. This checkpoint gives decent results for Hindi-english translation.