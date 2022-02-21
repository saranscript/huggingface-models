Used [run.sh](https://huggingface.co/madlag/bert-large-uncased-whole-word-masking-finetuned-squadv2/blob/main/run.sh) used to train using transformers/example/question_answering code.

Evaluation results : F1= 85.85 , a much better result than the original 81.9 from the BERT paper, due to the use of the "whole-word-masking" variation.
```
{
    "HasAns_exact": 80.58367071524967,
    "HasAns_f1": 86.64594807945029,
    "HasAns_total": 5928,
    "NoAns_exact": 85.06307821698907,
    "NoAns_f1": 85.06307821698907,
    "NoAns_total": 5945,
    "best_exact": 82.82658131895899,
    "best_exact_thresh": 0.0,
    "best_f1": 85.85337995578023,
    "best_f1_thresh": 0.0,
    "epoch": 2.0,
    "eval_samples": 12134,
    "exact": 82.82658131895899,
    "f1": 85.85337995578037,
    "total": 11873
}
```