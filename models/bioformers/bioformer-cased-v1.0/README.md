---
language:
- en
license: apache-2.0
---


Bioformer is a lightweight BERT model for biomedical text mining. Bioformer uses a biomedical vocabulary and is pre-trained from scratch only on biomedical domain corpora. Our experiments show that Bioformer is 3x as fast as BERT-base, and achieves comparable or even better performance than BioBERT/PubMedBERT on downstream NLP tasks.

Bioformer has 8 layers (transformer blocks) with a hidden embedding size of 512, and the number of self-attention heads is 8. Its total number of parameters is 42,820,610.

## Vocabulary of Bioformer
Bioformer uses a cased WordPiece vocabulary trained from a biomedical corpus, which included all PubMed abstracts (33 million, as of Feb 1, 2021) and 1 million PMC full-text articles. PMC has 3.6 million articles but we down-sampled them to 1 million such that the total size of PubMed abstracts and PMC full-text articles are approximately equal. To mitigate the out-of-vocabulary issue and include special symbols (e.g. male and female symbols) in biomedical literature, we trained Bioformer’s vocabulary from the Unicode text of the two resources. The vocabulary size of Bioformer is 32768 (2^15), which is similar to that of the original BERT.

## Pre-training of Bioformer
Bioformer was pre-trained from scratch on the same corpus as the vocabulary (33 million PubMed abstracts + 1 million PMC full-text articles). For the masked language modeling (MLM) objective, we used whole-word masking with a masking rate of 15%. There are debates on whether the next sentence prediction (NSP) objective could improve the performance on downstream tasks. We include it in our pre-training experiment in case the prediction of the next sentence is needed by end-users. Sentence segmentation of all training text was performed using [SciSpacy](https://allenai.github.io/scispacy/).

Pre-training of Bioformer was performed on a single Cloud TPU device (TPUv2, 8 cores, 8GB memory per core). The maximum input sequence length was fixed to 512, and the batch size was set to 256. We pre-trained Bioformer for 2 million steps, which took about 8.3 days.


## Awards

Bioformer achieved top performance (highest micro-F1 score) in the BioCreative VII COVID-19 multi-label topic classification challenge (https://biocreative.bioinformatics.udel.edu/media/store/files/2021/TRACK5_pos_1_BC7_submission_221.pdf)

## Acknowledgment

Bioformer is partly supported by the Google TPU Research Cloud (TRC) program.

## Questions
If you have any questions, please submit an issue here: https://github.com/WGLab/bioformer/issues

You can also send an email to Li Fang (fangli2718@gmail.com)