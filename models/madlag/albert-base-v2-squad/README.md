Albert v2 finetuned on SQuAD v1. 

Trained using the [nn_pruning](https://github.com/huggingface/nn_pruning/tree/main/examples/question_answering) script, with pruning disabled.

[Original results](https://github.com/google-research/albert) are F1=90.2, EM=83.2, we improved them to:

```{
    "exact_match": 83.74645222327341,
    "f1": 90.78776054621733
}```