This model is a T5-3B reranker, initialized with our pointwise ranker, [castorini/monot5-3b-msmarco](https://huggingface.co/castorini/monot5-3b-msmarco), and finetuned on the MS MARCO passage dataset for 50K steps (or 5 epochs) on the pairwise reranking task.

For more details on how to use it, check [pygaggle.ai](pygaggle.ai)!

Paper describing the model: [The Expando-Mono-Duo Design Pattern for Text Ranking with Pretrained Sequence-to-Sequence Models](https://arxiv.org/abs/2101.05667)