---
language: 
- kin
tags:
- NER
datasets:
- masakhaner
metrics:
- f1
- precision
- recall
license: apache-2.0
widget:
- text: "Ambasaderi Bellomo yavuze ko bishimira ubufatanye burambye hagati ya EU n’u Rwanda, bushingiye nanone ku bufatanye hagati y’imigabane ya Afurika n’u Burayi."
---

# Model description
**bert-base-uncased-kin** is a model based on the fine-tuned BERT base uncased model. It has been trained to recognize four types of entities:

- dates & time (DATE)
- Location (LOC)
- Organizations (ORG)
- Person (PER)

# Intended Use
- Intended to be used for research purposes concerning Named Entity Recognition for African Languages.
- Not intended for practical purposes.

# Training Data
This model was fine-tuned on the Kinyarwanda corpus **(kin)** of the [MasakhaNER](https://github.com/masakhane-io/masakhane-ner) dataset. However, we thresholded the number of entity groups per sentence in this dataset to 10 entity groups.

# Training procedure
This model was trained on a single NVIDIA P5000 from [Paperspace](https://www.paperspace.com)
#### Hyperparameters
- **Learning Rate:** 5e-5
- **Batch Size:** 32
- **Maximum Sequence Length:** 164
- **Epochs:** 30


# Evaluation Data
We evaluated this model on the test split of the Kinyarwandan corpus **(kin)** present in the [MasakhaNER](https://github.com/masakhane-io/masakhane-ner) with no thresholding.

# Metrics
- Precision
- Recall
- F1-score

# Limitations
- The size of the pre-trained language model prevents its usage in anything other than research.
- Lack of analysis concerning the bias and fairness in these models may make them dangerous if deployed into production system.
- The train data is a less populated version of the original dataset in terms of entity groups per sentence. Therefore, this can negatively impact the performance.

# Caveats and Recommendations
- The topics in the dataset corpus are centered around **News**. Future training could be done with a more diverse corpus.

# Results
Model Name| Precision | Recall | F1-score
-|-|-|-
**bert-base-uncased-kin**| 75.00 |80.09|77.47

# Usage

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("arnolfokam/bert-base-uncased-kin")
model = AutoModelForTokenClassification.from_pretrained("arnolfokam/bert-base-uncased-kin")

nlp = pipeline("ner", model=model, tokenizer=tokenizer)
example = "Rayon Sports yasinyishije rutahizamu w’Umurundi"

ner_results = nlp(example)
print(ner_results)
```