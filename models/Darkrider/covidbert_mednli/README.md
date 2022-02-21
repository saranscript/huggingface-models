# CovidBERT-MedNLI

This is the model **CovidBERT** trained by DeepSet on AllenAI's [CORD19 Dataset](https://pages.semanticscholar.org/coronavirus-research) of scientific articles about coronaviruses.

The model uses the original BERT wordpiece vocabulary and was subsequently fine-tuned on the [SNLI](https://nlp.stanford.edu/projects/snli/) and the [MultiNLI](https://www.nyu.edu/projects/bowman/multinli/) datasets using the [`sentence-transformers` library](https://github.com/UKPLab/sentence-transformers/) to produce universal sentence embeddings [1] using the **average pooling strategy** and a **softmax loss**.
It is further fine-tuned on both MedNLI datasets available at Physionet. 

[ACL-BIONLP 2019](https://physionet.org/content/mednli-bionlp19/1.0.1/)

[MedNLI from MIMIC](https://physionet.org/content/mednli/1.0.0/)


Parameter details for the original training on CORD-19 are available on [DeepSet's MLFlow](https://public-mlflow.deepset.ai/#/experiments/2/runs/ba27d00c30044ef6a33b1d307b4a6cba)

**Base model**: `deepset/covid_bert_base` from HuggingFace's `AutoModel`.

