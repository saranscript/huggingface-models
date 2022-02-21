---
datasets: pib
widget:
- text: "હેય! હું વાસુદેવ ગુપ્તા છું"

---

mBART (a pre-trained model by Facebook) is pre-trained to de-noise multiple languages simultaneously with BART objective.

Checkpoint available in this repository is obtained after fine-tuning `facebook/mbart-large-cc25` on all samples (~60K) from Bhasha (pib_v1.3) Gujarati-English parallel corpus. This checkpoint gives decent results for Gujarati-english translation.