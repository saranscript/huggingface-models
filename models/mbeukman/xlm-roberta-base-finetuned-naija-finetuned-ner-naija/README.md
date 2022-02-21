---
language: 
  - pcm
tags:
- NER
datasets:
- masakhaner
metrics:
- f1
- precision
- recall
widget:
- text: "Mixed Martial Arts joinbodi , Ultimate Fighting Championship , UFC don decide say dem go enta back di octagon on Saturday , 9 May , for Jacksonville , Florida ."
---


# xlm-roberta-base-finetuned-naija-finetuned-ner-naija
This is a token classification (specifically NER) model that fine-tuned [xlm-roberta-base-finetuned-naija](https://huggingface.co/Davlan/xlm-roberta-base-finetuned-naija) on the [MasakhaNER](https://arxiv.org/abs/2103.11811) dataset, specifically the Nigerian Pidgin part.

More information, and other similar models can be found in the [main Github repository](https://github.com/Michael-Beukman/NERTransfer).

## About
This model is transformer based and was fine-tuned on the MasakhaNER dataset. It is a named entity recognition dataset, containing mostly news articles in 10 different African languages. 
The model was fine-tuned for 50 epochs, with a maximum sequence length of 200, 32 batch size, 5e-5 learning rate. This process was repeated 5 times (with different random seeds), and this uploaded model performed the best out of those 5 seeds (aggregate F1 on test set).

This model was fine-tuned by me, Michael Beukman while doing a project at the University of the Witwatersrand, Johannesburg. This is version 1, as of 20 November 2021.
This model is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).

### Contact & More information
For more information about the models, including training scripts, detailed results and further resources, you can visit the the [main Github repository](https://github.com/Michael-Beukman/NERTransfer). You can contact me by filing an issue on this repository.

### Training Resources
In the interest of openness, and reporting resources used, we list here how long the training process took, as well as what the minimum resources would be to reproduce this. Fine-tuning each model on the NER dataset took between 10 and 30 minutes, and was performed on a NVIDIA RTX3090 GPU. To use a batch size of 32, at least 14GB of GPU memory was required, although it was just possible to fit these models in around 6.5GB's of VRAM when using a batch size of 1.


## Data
The train, evaluation and test datasets were taken directly from the MasakhaNER [Github](https://github.com/masakhane-io/masakhane-ner) repository, with minimal to no preprocessing, as the original dataset is already of high quality.
The motivation for the use of this data is that it is the "first large, publicly available, high­ quality dataset for named entity recognition (NER) in ten African languages" ([source](https://arxiv.org/pdf/2103.11811.pdf)). The high-quality data, as well as the groundwork laid by the paper introducing it are some more reasons why this dataset was used. For evaluation, the dedicated test split was used, which is from the same distribution as the training data, so this model may not generalise to other distributions, and further testing would need to be done to investigate this. The exact distribution of the data is covered in detail [here](https://arxiv.org/abs/2103.11811).

## Intended Use
This model are intended to be used for NLP research into e.g. interpretability or transfer learning. Using this model in production is not supported, as generalisability and downright performance is limited. In particular, this is not designed to be used in any important downstream task that could affect people, as harm could be caused by the limitations of the model, described next.

## Limitations
This model was only trained on one (relatively small) dataset, covering one task (NER) in one domain (news articles) and in a set span of time. The results may not generalise, and the model may perform badly, or in an unfair / biased way if used on other tasks. Although the purpose of this project was to investigate transfer learning, the performance on languages that the model was not trained for does suffer.


Because this model used xlm-roberta-base as its starting point (potentially with domain adaptive fine-tuning on specific languages), this model's limitations can also apply here. These can include being biased towards the hegemonic viewpoint of most of its training data, being ungrounded and having subpar results on other languages (possibly due to unbalanced training data).

As [Adelani et al. (2021)](https://arxiv.org/abs/2103.11811) showed, the models in general struggled with entities that were either longer than 3 words and entities that were not contained in the training data. This could bias the models towards not finding, e.g. names of people that have many words, possibly leading to a misrepresentation in the results. Similarly, names that are uncommon, and may not have been found in the training data (due to e.g. different languages) would also be predicted less often.


Additionally, this model has not been verified in practice, and other, more subtle problems may become prevalent if used without any verification that it does what it is supposed to.

### Privacy & Ethical Considerations
The data comes from only publicly available news sources, the only available data should cover public figures and those that agreed to be reported on. See the original MasakhaNER paper for more details.

No explicit ethical considerations or adjustments were made during fine-tuning of this model.

## Metrics
The language adaptive models achieve (mostly) superior performance over starting with xlm-roberta-base. Our main metric was the aggregate F1 score for all NER categories.

These metrics are on the test set for MasakhaNER, so the data distribution is similar to the training set, so these results do not directly indicate how well these models generalise.
We do find large variation in transfer results when starting from different seeds (5 different seeds were tested), indicating that the fine-tuning process for transfer might be unstable.

The metrics used were chosen to be consistent with previous work, and to facilitate research. Other metrics may be more appropriate for other purposes.
## Caveats and Recommendations
In general, this model performed worse on the 'date' category compared to others, so if dates are a critical factor, then that might need to be taken into account and addressed, by for example collecting and annotating more data.

## Model Structure
Here are some performance details on this specific model, compared to others we trained.
All of these metrics were calculated on the test set, and the seed was chosen that gave the best overall F1 score. The first three result columns are averaged over all categories, and the latter 4 provide performance broken down by category.

This model can predict the following label for a token ([source](https://huggingface.co/Davlan/xlm-roberta-large-masakhaner)):


Abbreviation|Description
-|-
O|Outside of a named entity
B-DATE |Beginning of a DATE entity right after another DATE entity
I-DATE |DATE entity
B-PER |Beginning of a person’s name right after another person’s name
I-PER |Person’s name
B-ORG |Beginning of an organisation right after another organisation
I-ORG |Organisation
B-LOC |Beginning of a location right after another location
I-LOC |Location



| Model Name                                         | Staring point        | Evaluation / Fine-tune Language  | F1 | Precision | Recall | F1 (DATE) | F1 (LOC) | F1 (ORG) | F1 (PER) |
| -------------------------------------------------- | -------------------- | -------------------- | -------------- | -------------- | -------------- | -------------- | -------------- | -------------- | -------------- |
| [xlm-roberta-base-finetuned-naija-finetuned-ner-naija](https://huggingface.co/mbeukman/xlm-roberta-base-finetuned-naija-finetuned-ner-naija) (This model) | [pcm](https://huggingface.co/Davlan/xlm-roberta-base-finetuned-naija) | pcm                  | 88.06          | 87.04          | 89.12          | 90.00          | 88.00          | 81.00          | 92.00          |
| [xlm-roberta-base-finetuned-swahili-finetuned-ner-naija](https://huggingface.co/mbeukman/xlm-roberta-base-finetuned-swahili-finetuned-ner-naija) | [swa](https://huggingface.co/Davlan/xlm-roberta-base-finetuned-swahili) | pcm                  | 89.12          | 87.84          | 90.42          | 90.00          | 89.00          | 82.00          | 94.00          |
| [xlm-roberta-base-finetuned-ner-naija](https://huggingface.co/mbeukman/xlm-roberta-base-finetuned-ner-naija) | [base](https://huggingface.co/xlm-roberta-base) | pcm                  | 88.89          | 88.13          | 89.66          | 92.00          | 87.00          | 82.00          | 94.00          |
## Usage
To use this model (or others), you can do the following, just changing the model name ([source](https://huggingface.co/dslim/bert-base-NER)):

```
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline
model_name = 'mbeukman/xlm-roberta-base-finetuned-naija-finetuned-ner-naija'
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForTokenClassification.from_pretrained(model_name)

nlp = pipeline("ner", model=model, tokenizer=tokenizer)
example = "Mixed Martial Arts joinbodi , Ultimate Fighting Championship , UFC don decide say dem go enta back di octagon on Saturday , 9 May , for Jacksonville , Florida ."

ner_results = nlp(example)
print(ner_results)
```
