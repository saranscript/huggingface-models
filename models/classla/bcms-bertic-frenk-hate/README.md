---
language: "hr"

tags:
- text-classification
- hate-speech

widget:
- text: "Potpredsjednik Vlade i ministar branitelja Tomo Medved komentirao je Vladine planove za zakonsku zabranu pozdrava 'za dom spremni'."
---
# bcms-bertic-frenk-hate

Text classification model based on [`classla/bcms-bertic`](https://huggingface.co/classla/bcms-bertic) and fine-tuned on the [FRENK dataset](https://www.clarin.si/repository/xmlui/handle/11356/1433) comprising of LGBT and migrant hatespeech. Only the Croatian subset of the data was used for fine-tuning and the dataset has been relabeled for binary classification (offensive or acceptable).




## Fine-tuning hyperparameters

Fine-tuning was performed with `simpletransformers`. Beforehand a brief hyperparameter optimisation was performed and the presumed optimal hyperparameters are:

```python

model_args = {
        "num_train_epochs": 12,
        "learning_rate": 1e-5,
        "train_batch_size": 74}
```

## Performance

The same pipeline was run with two other transformer models and `fasttext` for comparison. Accuracy and macro F1 score were recorded for each of the 6 fine-tuning sessions and post festum analyzed.

| model | average accuracy | average macro F1|
|---|---|---|
|bcms-bertic-frenk-hate|0.8313|0.8219|
|EMBEDDIA/crosloengual-bert |0.8054|0.796|
|xlm-roberta-base |0.7175|0.7049|
|fasttext|0.771 |0.754 |



From recorded accuracies and macro F1 scores p-values were also calculated:

Comparison with `crosloengual-bert`:

| test | accuracy p-value | macro F1 p-value|
| --- | --- | --- |
|Wilcoxon|0.00781|0.00781|
|Mann Whithney|0.00108|0.00108|
|Student t-test |2.43e-10 |1.27e-10|

Comparison with `xlm-roberta-base`:

| test | accuracy p-value | macro F1 p-value|
| --- | --- | --- |
|Wilcoxon|0.00781|0.00781|
|Mann Whithney|0.00107|0.00108|
|Student t-test |4.83e-11 | 5.61e-11 |



## Use examples

```python
from simpletransformers.classification import ClassificationModel
model_args = {
        "num_train_epochs": 12,
        "learning_rate": 1e-5,
        "train_batch_size": 74}

model = ClassificationModel(
    "bert", "5roop/bcms-bertic-frenk-hate", use_cuda=True,
    args=model_args
    
)

predictions, logit_output = model.predict(['Ne odbacujem da će RH primiti još migranata iz Afganistana, no neće biti novog vala',
                                           "Potpredsjednik Vlade i ministar branitelja Tomo Medved komentirao je Vladine planove za zakonsku zabranu pozdrava 'za dom spremni' "])
predictions
### Output:
### array([0, 0])
```

## Citation

If you use the model, please cite the following paper on which the original model is based:
```
@inproceedings{ljubesic-lauc-2021-bertic,
    title = "{BERT}i{\'c} - The Transformer Language Model for {B}osnian, {C}roatian, {M}ontenegrin and {S}erbian",
    author = "Ljube{\v{s}}i{\'c}, Nikola  and Lauc, Davor",
    booktitle = "Proceedings of the 8th Workshop on Balto-Slavic Natural Language Processing",
    month = apr,
    year = "2021",
    address = "Kiyv, Ukraine",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2021.bsnlp-1.5",
    pages = "37--42",
}
```

and the dataset used for fine-tuning:
```
@misc{ljubešić2019frenk,
      title={The FRENK Datasets of Socially Unacceptable Discourse in Slovene and English}, 
      author={Nikola Ljubešić and Darja Fišer and Tomaž Erjavec},
      year={2019},
      eprint={1906.02045},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/1906.02045}
}
```
