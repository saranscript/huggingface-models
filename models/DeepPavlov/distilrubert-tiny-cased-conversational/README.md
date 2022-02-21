---
language:
- ru
---
# distilrubert-small-cased-conversational
Conversational DistilRuBERT-small \(Russian, cased, 2‑layer, 768‑hidden, 12‑heads, 107M parameters\) was trained on OpenSubtitles\[1\], [Dirty](https://d3.ru/), [Pikabu](https://pikabu.ru/), and a Social Media segment of Taiga corpus\[2\] (as [Conversational RuBERT](https://huggingface.co/DeepPavlov/rubert-base-cased-conversational)). It can be considered as small copy of [Conversational DistilRuBERT-base](https://huggingface.co/DeepPavlov/distilrubert-base-cased-conversational).

Our DistilRuBERT-small was highly inspired by \[3\], \[4\]. Namely, we used 
* KL loss (between teacher and student output logits)
* MLM loss (between tokens labels and student output logits)
* Cosine embedding loss (between averaged six consecutive hidden states from teacher's encoder and one hidden state of the student)
* MSE loss (between averaged six consecutive attention maps from teacher's encoder and one attention map of the student)

The model was trained for about 80 hrs. on 8 nVIDIA Tesla P100-SXM2.0 16Gb.

To evaluate improvements in the inference speed, we ran teacher and student models on random sequences with seq_len=512, batch_size = 16 (for throughput) and batch_size=1 (for latency). 
All tests were performed on Intel(R) Xeon(R) CPU E5-2698 v4 @ 2.20GHz and nVIDIA Tesla P100-SXM2.0 16Gb.

| Model                                           | Size, Mb.  | CPU latency, sec.| GPU latency, sec. | CPU throughput, samples/sec. | GPU throughput, samples/sec. |
|-------------------------------------------------|------------|------------------|-------------------|------------------------------|------------------------------|
| Teacher (RuBERT-base-cased-conversational)      | 679        | 0.655            | 0.031             | 0.3754                       | 36.4902                      |
| Student (DistilRuBERT-small-cased-conversational)| 409        | 0.1656           | 0.015             | 0.9692                       | 71.3553                      |


To evaluate model quality, we fine-tuned DistilRuBERT-small on classification, NER and question answering tasks. Scores and archives with fine-tuned models can be found in [DeepPavlov docs](http://docs.deeppavlov.ai/en/master/features/overview.html#models).

\[1\]: P. Lison and J. Tiedemann, 2016, OpenSubtitles2016: Extracting Large Parallel Corpora from Movie and TV Subtitles. In Proceedings of the 10th International Conference on Language Resources and Evaluation \(LREC 2016\)

\[2\]: Shavrina T., Shapovalova O. \(2017\) TO THE METHODOLOGY OF CORPUS CONSTRUCTION FOR MACHINE LEARNING: «TAIGA» SYNTAX TREE CORPUS AND PARSER. in proc. of “CORPORA2017”, international conference , Saint-Petersbourg, 2017.

\[3\]: Sanh, V., Debut, L., Chaumond, J., & Wolf, T. \(2019\). DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter. arXiv preprint arXiv:1910.01108.

\[4\]: <https://github.com/huggingface/transformers/tree/master/examples/research_projects/distillation>