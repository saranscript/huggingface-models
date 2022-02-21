# FrugalScore
FrugalScore is an approach to learn a fixed, low cost version of any expensive NLG metric, while retaining most of its original performance

Paper: https://arxiv.org/abs/2110.08559?context=cs

Project github: https://github.com/moussaKam/FrugalScore

The pretrained checkpoints presented in the paper :

| FrugalScore                                        | Student     | Teacher        | Method     |
|----------------------------------------------------|-------------|----------------|------------|
| [moussaKam/frugalscore_tiny_bert-base_bert-score](https://huggingface.co/moussaKam/frugalscore_tiny_bert-base_bert-score)    | BERT-tiny   | BERT-Base      | BERTScore  |
| [moussaKam/frugalscore_small_bert-base_bert-score](https://huggingface.co/moussaKam/frugalscore_small_bert-base_bert-score)   | BERT-small  | BERT-Base      | BERTScore  |
| [moussaKam/frugalscore_medium_bert-base_bert-score](https://huggingface.co/moussaKam/frugalscore_medium_bert-base_bert-score) | BERT-medium | BERT-Base      | BERTScore  |
| [moussaKam/frugalscore_tiny_roberta_bert-score](https://huggingface.co/moussaKam/frugalscore_tiny_roberta_bert-score)     | BERT-tiny   | RoBERTa-Large  | BERTScore  |
| [moussaKam/frugalscore_small_roberta_bert-score](https://huggingface.co/moussaKam/frugalscore_small_roberta_bert-score)     | BERT-small  | RoBERTa-Large  | BERTScore  |
| [moussaKam/frugalscore_medium_roberta_bert-score](https://huggingface.co/moussaKam/frugalscore_medium_roberta_bert-score)    | BERT-medium | RoBERTa-Large  | BERTScore  |
| [moussaKam/frugalscore_tiny_deberta_bert-score](https://huggingface.co/moussaKam/frugalscore_tiny_deberta_bert-score)      | BERT-tiny   | DeBERTa-XLarge | BERTScore  |
| [moussaKam/frugalscore_small_deberta_bert-score](https://huggingface.co/moussaKam/frugalscore_small_deberta_bert-score)     | BERT-small  | DeBERTa-XLarge | BERTScore  |
| [moussaKam/frugalscore_medium_deberta_bert-score](https://huggingface.co/moussaKam/frugalscore_medium_deberta_bert-score)    | BERT-medium | DeBERTa-XLarge | BERTScore  |
| [moussaKam/frugalscore_tiny_bert-base_mover-score](https://huggingface.co/moussaKam/frugalscore_tiny_bert-base_mover-score)   | BERT-tiny   | BERT-Base      | MoverScore |
| [moussaKam/frugalscore_small_bert-base_mover-score](https://huggingface.co/moussaKam/frugalscore_small_bert-base_mover-score)  | BERT-small  | BERT-Base      | MoverScore |
| [moussaKam/frugalscore_medium_bert-base_mover-score](https://huggingface.co/moussaKam/frugalscore_medium_bert-base_mover-score) | BERT-medium | BERT-Base      | MoverScore |