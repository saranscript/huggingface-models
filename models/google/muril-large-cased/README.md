# MuRIL Large
Multilingual Representations for Indian Languages : A BERT Large (24L) model pre-trained on 17 Indian languages, and their transliterated counterparts.

## Overview

This model uses a BERT large architecture [1] pretrained from scratch using the
Wikipedia [2], Common Crawl [3], PMINDIA [4] and Dakshina [5] corpora for 17 [6]
Indian languages.

We use a training paradigm similar to multilingual bert, with a few
modifications as listed:

*   We include translation and transliteration segment pairs in training as
    well.
*   We keep an exponent value of 0.3 and not 0.7 for upsampling, shown to
    enhance low-resource performance. [7]

See the Training section for more details.

## Training

The MuRIL model is pre-trained on monolingual segments as well as parallel
segments as detailed below :

*   Monolingual Data : We make use of publicly available corpora from Wikipedia
    and Common Crawl for 17 Indian languages.
*   Parallel Data : We have two types of parallel data :
    *   Translated Data : We obtain translations of the above monolingual
        corpora using the Google NMT pipeline. We feed translated segment pairs
        as input. We also make use of the publicly available PMINDIA corpus.
    *   Transliterated Data : We obtain transliterations of Wikipedia using the
        IndicTrans [8] library. We feed transliterated segment pairs as input.
        We also make use of the publicly available Dakshina dataset.

We keep an exponent value of 0.3 to calculate duplication multiplier values for
upsampling of lower resourced languages and set dupe factors accordingly. Note,
we limit transliterated pairs to Wikipedia only.

The model was trained using a self-supervised masked language modeling task. We
do whole word masking with a maximum of 80 predictions. The model was trained
for 1500K steps, with a batch size of 8192, and a max sequence length of 512.

### Trainable parameters

All parameters in the module are trainable, and fine-tuning all parameters is
the recommended practice.


## Uses & Limitations

This model is intended to be used for a variety of downstream NLP tasks for
Indian languages. This model is trained on transliterated data as well, a
phenomenon commonly observed in the Indian context. This model is not expected
to perform well on languages other than the ones used in pre-training, i.e. 17
Indian languages.

## Evaluation

We provide the results of fine-tuning this model on a set of downstream tasks.<br/>
We choose these tasks from the XTREME benchmark, with evaluation done on Indian language test-sets.<br/>
All results are computed in a zero-shot setting, with English being the high resource training set language.<br/>
The results for XLM-R (Large) are taken from the XTREME paper [9].

*   Shown below are results on datasets from the XTREME benchmark (in %)
    <br/>

    PANX (F1)     | bn   | en   | hi   | ml   | mr   | ta   | te   | ur   | Average
    :------------ | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ------:
    XLM-R (large) | 78.8 | 84.7 | 73.0 | 67.8 | 68.1 | 59.5 | 55.8 | 56.4 | 68.0
    MuRIL (large) | 85.8 | 85.0 | 78.3 | 75.6 | 77.3 | 71.1 | 65.6 | 83.0 | 77.7

    <br/>

    UDPOS (F1)    | en   | hi   | mr   | ta   | te   | ur   | Average
    :------------ | ---: | ---: | ---: | ---: | ---: | ---: | ------:
    XLM-R (large) | 96.1 | 76.4 | 80.8 | 65.2 | 86.6 | 70.3 | 79.2
    MuRIL (large) | 95.7 | 71.3 | 85.7 | 62.6 | 85.8 | 62.8 | 77.3

    <br/>

    XNLI (Accuracy) | en   | hi   | ur   | Average
    :-------------- | ---: | ---: | ---: | ------:
    XLM-R (large)   | 88.7 | 75.6 | 71.7 | 78.7
    MuRIL (large)   | 88.4 | 75.8 | 71.7 | 78.6

    <br/>

    XQUAD (F1/EM) | en        | hi        | Average
    :------------ | --------: | --------: | --------:
    XLM-R (large) | 86.5/75.7 | 76.7/59.7 | 81.6/67.7
    MuRIL (large) | 88.2/77.8 | 78.4/62.4 | 83.3/70.1

    <br/>

    MLQA (F1/EM)  | en        | hi        | Average
    :------------ | --------: | --------: | --------:
    XLM-R (large) | 83.5/70.6 | 70.6/53.1 | 77.1/61.9
    MuRIL (large) | 84.4/71.7 | 72.2/54.1 | 78.3/62.9

    <br/>

    TyDiQA (F1/EM) | en        | bn        | te        | Average
    :------------- | --------: | --------: | --------: | --------:
    XLM-R (large)  | 71.5/56.8 | 64.0/47.8 | 70.1/43.6 | 68.5/49.4
    MuRIL (large)  | 75.9/66.8 | 67.1/53.1 | 71.5/49.8 | 71.5/56.6

    <br/>

    The fine-tuning hyperparameters are as follows:

    Task   | Batch Size | Learning Rate | Epochs | Warm-up Ratio
    :----- | ---------: | ------------: | -----: | ------------:
    PANX   | 32         | 2e-5          | 10     | 0.1
    UDPOS  | 64         | 5e-6          | 10     | 0.1
    XNLI   | 128        | 2e-5          | 5      | 0.1
    XQuAD  | 32         | 3e-5          | 2      | 0.1
    MLQA   | 32         | 3e-5          | 2      | 0.1
    TyDiQA | 32         | 3e-5          | 3      | 0.1

## References

\[1]: Jacob Devlin, Ming-Wei Chang, Kenton Lee, Kristina Toutanova. [BERT:
Pre-training of Deep Bidirectional Transformers for Language
Understanding](https://arxiv.org/abs/1810.04805). arXiv preprint
arXiv:1810.04805, 2018.

\[2]: [Wikipedia](https://www.tensorflow.org/datasets/catalog/wikipedia)

\[3]: [Common Crawl](http://commoncrawl.org/the-data/)

\[4]:
[PMINDIA](http://lotus.kuee.kyoto-u.ac.jp/WAT/indic-multilingual/index.html)

\[5]: [Dakshina](https://github.com/google-research-datasets/dakshina)

\[6]: Assamese (as), Bengali (bn), English (en), Gujarati (gu), Hindi (hi),
Kannada (kn), Kashmiri (ks), Malayalam (ml), Marathi (mr), Nepali (ne), Oriya
(or), Punjabi (pa), Sanskrit (sa), Sindhi (sd), Tamil (ta), Telugu (te) and Urdu
(ur).

\[7]: Conneau, Alexis, et al.
[Unsupervised cross-lingual representation learning at scale](https://arxiv.org/pdf/1911.02116.pdf).
arXiv preprint arXiv:1911.02116 (2019).

\[8]: [IndicTrans](https://github.com/libindic/indic-trans)

\[9]: Hu, J., Ruder, S., Siddhant, A., Neubig, G., Firat, O., & Johnson, M.
(2020). [Xtreme: A massively multilingual multi-task benchmark for evaluating
cross-lingual generalization.](https://arxiv.org/pdf/2003.11080.pdf) arXiv
preprint arXiv:2003.11080.

\[10]: Fang, Y., Wang, S., Gan, Z., Sun, S., & Liu, J. (2020).
[FILTER: An Enhanced Fusion Method for Cross-lingual Language Understanding.](https://arxiv.org/pdf/2009.05166.pdf)
arXiv preprint arXiv:2009.05166.

## Citation

If you find MuRIL useful in your applications, please cite the following paper:

```
@misc{khanuja2021muril,
      title={MuRIL: Multilingual Representations for Indian Languages},
      author={Simran Khanuja and Diksha Bansal and Sarvesh Mehtani and Savya Khosla and Atreyee Dey and Balaji Gopalan and Dilip Kumar Margam and Pooja Aggarwal and Rajiv Teja Nagipogu and Shachi Dave and Shruti Gupta and Subhash Chandra Bose Gali and Vish Subramanian and Partha Talukdar},
      year={2021},
      eprint={2103.10730},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

## Contact

Please mail your queries/feedback to muril-contact@google.com.
