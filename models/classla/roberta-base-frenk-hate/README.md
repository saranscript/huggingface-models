---

language: "en"

tags:
- text-classification
- hate-speech

widget:
- text: "Gay is okay."
---




# roberta-base-frenk-hate

Text classification model based on [`roberta-base`](https://huggingface.co/roberta-base) and fine-tuned on the [FRENK dataset](https://www.clarin.si/repository/xmlui/handle/11356/1433) comprising of LGBT and migrant hatespeech. Only the English subset of the data was used for fine-tuning and the dataset has been relabeled for binary classification (offensive or acceptable).

## Fine-tuning hyperparameters

Fine-tuning was performed with `simpletransformers`. Beforehand a brief hyperparameter optimisation was performed and the presumed optimal hyperparameters are:

```python
model_args = {
        "num_train_epochs": 6,
        "learning_rate": 3e-6,
        "train_batch_size": 69}
```

## Performance

The same pipeline was run with two other transformer models and `fasttext` for comparison. Accuracy and macro F1 score were recorded for each of the 6 fine-tuning sessions and post festum analyzed.

| model | average accuracy | average macro F1|
|---|---|---|
|roberta-base-frenk-hate|0.7915|0.7785|
|xlm-roberta-large |0.7904|0.77876|
|xlm-roberta-base |0.7577|0.7402|
|fasttext|0.725 |0.707 |



From recorded accuracies and macro F1 scores p-values were also calculated:

Comparison with `xlm-roberta-base`:

| test | accuracy p-value | macro F1 p-value|
| --- | --- | --- |
|Wilcoxon|0.00781|0.00781|
|Mann Whithney U-test|0.00108|0.00108|
|Student t-test | 1.35e-08 | 1.05e-07|


Comparison with `xlm-roberta-large` yielded inconclusive results.  `roberta-base` has average accuracy 0.7915, while `xlm-roberta-large` has average accuracy of 0.7904. If macro F1 scores were to be compared, `roberta-base` actually has lower average than `xlm-roberta-large`: 0.77852 vs 0.77876 respectively. The same statistical tests were performed with the premise that `roberta-base` has greater metrics, and the results are given below.

| test | accuracy p-value | macro F1 p-value|
| --- | --- | --- |
|Wilcoxon|0.188|0.406|
|Mann Whithey|0.375|0.649|
|Student t-test | 0.681| 0.934|

With reversed premise (i.e., that `xlm-roberta-large` has greater statistics) the Wilcoxon p-value for macro F1 scores for this case reaches 0.656, Mann-Whithey p-value is 0.399, and of course the Student p-value stays the same. It was therefore concluded that performance of the two models are not statistically significantly different from one another.

## Use examples

```python
from simpletransformers.classification import ClassificationModel
model_args = {
        "num_train_epochs": 6,
        "learning_rate": 3e-6,
        "train_batch_size": 69}

model = ClassificationModel(
    "roberta", "5roop/roberta-base-frenk-hate", use_cuda=True,
    args=model_args
    
)

predictions, logit_output = model.predict(["Build the wall", 
                                        "Build the wall of trust"]
                                        )
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


