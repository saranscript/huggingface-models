---
language:
- en
tags:
- pubmed
- cancer
- gene
- clinical trial
- bioinformatic
license: apache-2.0
datasets:
- pubmed
widget:
- text: "The <mask> effects of hyperatomarin"
---

# Roberta-Base fine-tuned on [PubMed](https://pubmed.ncbi.nlm.nih.gov/) Abstract
> We limit the training textual data to the following [MeSH](https://www.ncbi.nlm.nih.gov/mesh/)
* All the child MeSH of ```Biomarkers, Tumor(D014408)```, including things like ```Carcinoembryonic Antigen(D002272)```
* All the child MeSH of ```Carcinoma(D002277)```, including things like all kinds of carcinoma: like ```Carcinoma, Lewis Lung(D018827)``` etc. around 80 kinds of carcinoma
* All the child MeSH of ```Clinical Trial(D016439)```
* The training text file amounts to 531Mb
## Training
* Trained on language modeling task, with ```mlm_probability=0.15```, on 2 Tesla V100 32G
```python
training_args = TrainingArguments(
    output_dir=config.save, #select model path for checkpoint
    overwrite_output_dir=True,
    num_train_epochs=3,
    per_device_train_batch_size=30,
    per_device_eval_batch_size=60,
    evaluation_strategy= 'steps',
    save_total_limit=2,
    eval_steps=250,
    metric_for_best_model='eval_loss',
    greater_is_better=False,
    load_best_model_at_end =True,
    prediction_loss_only=True,
    report_to = "none")
```