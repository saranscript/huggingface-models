---
language: 
  - en
thumbnail: "https://repository-images.githubusercontent.com/401779782/c2f46be5-b74b-4620-ad64-57487be3b1ab"
tags:
- text2sql
widget:
- "And the concert named Auditions? | concert_singer | stadium : stadium_id, location, name, capacity, highest, lowest, average | singer : sing       er_id, name, country, song_name, song_release_year, age, is_male | concert : concert_id, concert_name ( Super bootcamp, Auditions ), theme, stadium_id, year | singer_in_concert : concert_id, singer_id || Which year did the concert Super bootcamp happen in? | Find the name and location of the stadiums which some concerts happened in the years of both 2014 and 2015."
- "How many singers do we have? | concert_singer | stadium : stadium_id, location, name, capacity, highest, lowest, average | singer : singer_id, name, country, song_name, song_release_year, age, is_male | concert : concert_id, concert_name, theme, stadium_id, year | singer_in_concert : concert_id, singer_id"
license: "apache-2.0"
datasets:
- cosql
- spider
metrics:
- cosql
---

## tscholak/2e826ioa

Fine-tuned weights for [PICARD - Parsing Incrementally for Constrained Auto-Regressive Decoding from Language Models](https://arxiv.org/abs/2109.05093) based on [T5-3B](https://huggingface.co/t5-3b).


### Training Data

The model has been fine-tuned on the 2,164 training dialogues in the [CoSQL SQL-grounded dialogue state tracking dataset](https://yale-lily.github.io/cosql) and the 7,000 training examples in the [Spider text-to-SQL dataset](https://yale-lily.github.io/spider). The model solves both, CoSQL's zero-shot text-to-SQL dialogue state tracking task and Spider's zero-shot text-to-SQL translation task. Zero-shot means that the model can generalize to unseen SQL databases.


### Training Objective

This model was initialized with [T5-3B](https://huggingface.co/t5-3b) and fine-tuned with the text-to-text generation objective.

A question is always grounded in both, a database schema and the preceiding questions in the dialogue. The model is trained to predict the SQL query that would be used to answer the user's current natural language question. The input to the model is composed of the user's current question, the database identifier, a list of tables and their columns, and a sequence of previous questions in reverse chronological order.

```
[current question] | [db_id] | [table] : [column] ( [content] , [content] ) , [column] ( ... ) , [...] | [table] : ... | ... || [previous question] | ... | [first question]
```
The sequence of previous questions is separated by `||` from the linearized schema. In the absence of previous questions (for example, for the first question in a dialogue or for Spider questions), this separator is omitted.

The model outputs the database identifier and the SQL query that will be executed on the database to answer the user's current question in the dialog.

```
[db_id] | [sql]
```


### Performance

Out of the box, this model achieves 53.8 % question match accuracy and 21.8 % interaction match accuracy on the CoSQL development set. On the CoSQL test set, the model achieves 51.4 % question match accuracy and 21.7 % interaction match accuracy.

Using the PICARD constrained decoding method (see [the official PICARD implementation](https://github.com/ElementAI/picard)), the model's performance can be improved to **56.9 %** question match accuracy and **24.2 %** interaction match accuracy on the CoSQL development set. On the CoSQL test set and with PICARD, the model achieves **54.6 %** question match accuracy and **23.7 %** interaction match accuracy.


### Usage

Please see [the official repository](https://github.com/ElementAI/picard) for scripts and docker images that support evaluation and serving of this model.


### References

1. [PICARD - Parsing Incrementally for Constrained Auto-Regressive Decoding from Language Models](https://arxiv.org/abs/2109.05093)

2. [Official PICARD code](https://github.com/ElementAI/picard)


### Citation

```bibtex
@inproceedings{Scholak2021:PICARD,
  author = {Torsten Scholak and Nathan Schucher and Dzmitry Bahdanau},
  title = "{PICARD}: Parsing Incrementally for Constrained Auto-Regressive Decoding from Language Models",
  booktitle = "Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing",
  month = nov,
  year = "2021",
  publisher = "Association for Computational Linguistics",
  url = "https://aclanthology.org/2021.emnlp-main.779",
  pages = "9895--9901",
}
```