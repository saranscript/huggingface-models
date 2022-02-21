# T5-Paraphrase pretrained using the CORD-19 dataset.

The base model is manueldeprada/t5-cord19, which has been pretrained with the text and abstracts from the CORD-19 dataset.

It has been finetuned in paraphrasing text like ceshine/t5-paraphrase-paws-msrp-opinosis, using the scripts from [ceshine/finetuning-t5 Github repo](https://github.com/ceshine/finetuning-t5/tree/master/paraphrase).

It does the same paraphrasing but the CORD-19 pretraining allows this model to perform well in COVID-19 related text.