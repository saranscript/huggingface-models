⚠️ **Disclaimer** ⚠️ 

This model is community-contributed, and not supported by Amazon, Inc.

## BORT

[Amazon's BORT](https://www.amazon.science/blog/a-version-of-the-bert-language-model-thats-20-times-as-fast)

BORT is a highly compressed version of [bert-large](https://huggingface.co/bert-large-uncased) that is up to 10 times faster at inference. 
The model is an optimal sub-architecture of *bert-large* that was found using neural architecture search.

[Paper](https://arxiv.org/abs/2010.10499)

**Abstract**

We extract an optimal subset of architectural parameters for the BERT architecture from Devlin et al. (2018) by applying recent breakthroughs in algorithms for neural architecture search. This optimal subset, which we refer to as "Bort", is demonstrably smaller, having an effective (that is, not counting the embedding layer) size of 5.5% the original BERT-large architecture, and 16% of the net size. Bort is also able to be pretrained in 288 GPU hours, which is 1.2% of the time required to pretrain the highest-performing BERT parametric architectural variant, RoBERTa-large (Liu et al., 2019), and about 33% of that of the world-record, in GPU hours, required to train BERT-large on the same hardware. It is also 7.9x faster on a CPU, as well as being better performing than other compressed variants of the architecture, and some of the non-compressed variants: it obtains performance improvements of between 0.3% and 31%, absolute, with respect to BERT-large, on multiple public natural language understanding (NLU) benchmarks.

The original model can be found under:
https://github.com/alexa/bort

**IMPORTANT**

BORT requires a very unique fine-tuning algorithm, called [Agora](https://adewynter.github.io/notes/bort_algorithms_and_applications.html) which is not open-sourced yet. 
Standard fine-tuning has not shown to work well in initial experiments, so stay tuned for updates!
