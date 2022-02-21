---
language: "sl"

tags:
- text-classification
- hate-speech

widget:
- text: "Silva, ti si grda in neprijazna"
---

Text classification model based on `EMBEDDIA/sloberta` and fine-tuned on the [FRENK dataset](https://www.clarin.si/repository/xmlui/handle/11356/1433) comprising of LGBT and migrant hatespeech. Only the slovenian subset of the data was used for fine-tuning and the dataset has been relabeled for binary classification (offensive or acceptable).

## Fine-tuning hyperparameters

Fine-tuning was performed with `simpletransformers`. Beforehand a brief hyperparameter optimisation was performed and the presumed optimal hyperparameters are:
```python
model_args = {
        "num_train_epochs": 14,
        "learning_rate": 1e-5,
        "train_batch_size": 21,
        }
```

## Performance

The same pipeline was run with two other transformer models and `fasttext` for comparison. Accuracy and macro F1 score were recorded for each of the 6 fine-tuning sessions and post festum analyzed.

| model | average accuracy | average macro F1|
|---|---|---|
|sloberta-frenk-hate|0.7785|0.7764|
|EMBEDDIA/crosloengual-bert |0.7616|0.7585|
|xlm-roberta-base |0.686|0.6827|
|fasttext|0.709 |0.701 |

From recorded accuracies and macro F1 scores p-values were also calculated:

Comparison with `crosloengual-bert`:

| test | accuracy p-value | macro F1 p-value|
| --- | --- | --- |
|Wilcoxon|0.00781|0.00781|
|Mann Whithney U test|0.00163|0.00108|
|Student t-test |0.000101|3.95e-05|

Comparison with `xlm-roberta-base`:

| test | accuracy p-value | macro F1 p-value|
| --- | --- | --- |
|Wilcoxon|0.00781|0.00781|
|Mann Whithney U test|0.00108|0.00108|
|Student t-test |9.46e-11|6.94e-11|
## Use examples

```python
from simpletransformers.classification import ClassificationModel
model_args = {
        "num_train_epochs": 6,
        "learning_rate": 3e-6,
        "train_batch_size": 69}

model = ClassificationModel(
    "camembert", "5roop/sloberta-frenk-hate", use_cuda=True,
    args=model_args
    
)

predictions, logit_output = model.predict(["Silva, ti si grda in neprijazna", "Naša hiša ima dimnik"])
predictions
### Output:
### array([1, 0])
```

## Citation

If you use the model, please cite the following paper on which the original model is based:

```
@article{DBLP:journals/corr/abs-1907-11692,
  author    = {Yinhan Liu and
               Myle Ott and
               Naman Goyal and
               Jingfei Du and
               Mandar Joshi and
               Danqi Chen and
               Omer Levy and
               Mike Lewis and
               Luke Zettlemoyer and
               Veselin Stoyanov},
  title     = {RoBERTa: {A} Robustly Optimized {BERT} Pretraining Approach},
  journal   = {CoRR},
  volume    = {abs/1907.11692},
  year      = {2019},
  url       = {http://arxiv.org/abs/1907.11692},
  archivePrefix = {arXiv},
  eprint    = {1907.11692},
  timestamp = {Thu, 01 Aug 2019 08:59:33 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-1907-11692.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
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