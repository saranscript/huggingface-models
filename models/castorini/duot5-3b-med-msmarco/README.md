This model is a T5-3B reranker pre-finetuned on the MS MARCO passage dataset for 10K steps (or 1 epoch) on the pairwise task and then finetuned on MedMARCO (from [Sledge-Z paper](https://www.aclweb.org/anthology/2020.emnlp-main.341.pdf)) for 1K steps on the pairwise task.

For more details on how to use it, check [pygaggle.ai](pygaggle.ai)!

Paper describing the model: [The Expando-Mono-Duo Design Pattern for Text Ranking with Pretrained Sequence-to-Sequence Models](https://arxiv.org/abs/2101.05667)