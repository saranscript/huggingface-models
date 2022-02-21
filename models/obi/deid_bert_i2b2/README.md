---
language:
  - en
thumbnail: "https://www.onebraveidea.org/wp-content/uploads/2019/07/OBI-Logo-Website.png"
tags:
- deidentification
- medical notes
datasets:
- I2B2
metrics:
- F1
- Recall
- AUC
widget:
- text: "Physician Discharge Summary Admit date: 10/12/1982 Discharge date: 10/22/1982 Patient Information Jack Reacher, 54 y.o. male (DOB = 1/21/1928)."
- text: "Home Address: 123 Park Drive, San Diego, CA, 03245. Home Phone: 202-555-0199 (home)."
- text: "Hospital Care Team Service: Orthopedics Inpatient Attending: Roger C Kelly, MD Attending phys phone: (634)743-5135 Discharge Unit: HCS843 Primary Care Physician: Hassan V Kim, MD 512-832-5025."
---


# BERT-based deidentification model

This repo contains model weights for clinical note de-deidentification trained on the I2B2 dataset. Note that the hosted inference API uses a different tokenizer than what we developed for this task.
Please see [OBI EHR deidentification](https://github.com/obi-ds/ehr_deidentification) for more details and how to get started.
