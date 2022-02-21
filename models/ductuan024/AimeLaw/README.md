<h1>BERT for Vietnamese Law</h1>

Apply for Task 1: Legal Document Retrieval on <a href="https://www.jaist.ac.jp/is/labs/nguyen-lab/home/alqac-2021/">ALQAC 2021</a> dataset

The model achieved 0.80 on the leaderboard(1st place score is 0.88).

We use <a href="https://huggingface.co/NlpHUST/vibert4news-base-cased">vibert4news</a> as based model and fine-tune on our own Vietnamese law dataset.

We use word sentencepiece, use basic bert tokenization and same config with bert base with lowercase = False.

