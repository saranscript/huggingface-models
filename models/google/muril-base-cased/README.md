---
thumbnail: https://huggingface.co/front/thumbnails/google.png
license: apache-2.0
---
MuRIL: Multilingual Representations for Indian Languages
===
MuRIL is a BERT model pre-trained on 17 Indian languages and their transliterated counterparts. We have released the pre-trained model (with the MLM layer intact, enabling masked word predictions) in this repository. We have also released the encoder on [TFHub](https://tfhub.dev/google/MuRIL/1) with an additional pre-processing module, that processes raw text into the expected input format for the encoder. You can find more details on MuRIL in this [paper](http://arxiv.org/abs/2103.10730).

## Overview

This model uses a BERT base architecture [1] pretrained from scratch using the
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
for 1000K steps, with a batch size of 4096, and a max sequence length of 512.

### Trainable parameters

All parameters in the module are trainable, and fine-tuning all parameters is
the recommended practice.

## Uses & Limitations

This model is intended to be used for a variety of downstream NLP tasks for
Indian languages. This model is trained on transliterated data as well, a
phenomomenon commonly observed in the Indian context. This model is not expected
to perform well on languages other than the ones used in pretraining, i.e. 17
Indian languages.

## Evaluation

We provide the results of fine-tuning this model on a set of downstream tasks.<br/>
We choose these tasks from the XTREME benchmark, with evaluation done on Indian language test-sets.<br/>
We also transliterate the test-sets and evaluate on the same.<br/>
We use the same fine-tuning setting as is used by [9], except for TyDiQA, where we use additional SQuAD v1.1 English training data, similar to [10].<br/>
For Tatoeba, we do not fine-tune the model, and use the pooled_output of the last layer as the sentence embedding.<br/>
All results are computed in a zero-shot setting, with English being the high resource training set language.

*   Shown below are results on datasets from the XTREME benchmark (in %)
    <br/>

    PANX (F1) | ml    | ta    | te    | en    | bn    | hi    | mr    | ur    | Average
    :-------- | ----: | ----: | ----: | ----: | ----: | ----: | ----: | ----: | ------:
    mBERT     | 54.77 | 51.24 | 50.16 | 84.40 | 68.59 | 65.13 | 58.44 | 31.36 | 58.01
    MuRIL     | 75.74 | 71.86 | 64.99 | 84.43 | 85.97 | 78.09 | 74.63 | 85.07 | 77.60

    <br/>

    UDPOS (F1) | en    | hi    | mr    | ta    | te    | ur    | Average
    :--------- | ----: | ----: | ----: | ----: | ----: | ----: | ------:
    mBERT      | 95.35 | 66.09 | 71.27 | 59.58 | 76.98 | 57.85 | 71.19
    MuRIL      | 95.55 | 64.47 | 82.95 | 62.57 | 85.63 | 58.93 | 75.02

    <br/>

    XNLI (Accuracy) | en    | hi    | ur    | Average
    :-------------- | ----: | ----: | ----: | ------:
    mBERT           | 81.72 | 60.52 | 58.20 | 66.81
    MuRIL           | 83.85 | 70.66 | 67.70 | 74.07

    <br/>

    Tatoeba (Accuracy) | ml    | ta    | te    | bn    | hi    | mr    | ur    | Average
    :----------------- | ----: | ----: | ----: | ----: | ----: | ----: | ----: | ------:
    mBERT              | 20.23 | 12.38 | 14.96 | 12.80 | 27.80 | 18.00 | 22.70 | 18.41
    MuRIL              | 26.35 | 36.81 | 17.52 | 20.20 | 31.50 | 26.60 | 17.10 | 25.15

    <br/>

    XQUAD (F1/EM) | en          | hi          | Average
    :------------ | ----------: | ----------: | ----------:
    mBERT         | 83.85/72.86 | 58.46/43.53 | 71.15/58.19
    MuRIL         | 84.31/72.94 | 73.93/58.32 | 79.12/65.63

    <br/>

    MLQA (F1/EM) | en          | hi          | Average
    :----------- | ----------: | ----------: | ----------:
    mBERT        | 80.39/67.30 | 50.28/35.18 | 65.34/51.24
    MuRIL        | 80.28/67.37 | 67.34/50.22 | 73.81/58.80

    <br/>

    TyDiQA (F1/EM)    | en          | bn          | te          | Average
    :---------------- | ----------: | ----------: | ----------: | ----------:
    mBERT             | 75.21/65.00 | 60.62/45.13 | 53.55/44.54 | 63.13/51.66
    MuRIL             | 74.10/64.55 | 78.03/66.37 | 73.95/46.94 | 75.36/59.28

*   Shown below are results on the transliterated versions of the above
    test-sets.

    PANX (F1) | ml_tr | ta_tr | te_tr | bn_tr | hi_tr | mr_tr | ur_tr | Average
    :-------- | ----: | ----: | ----: | ----: | ----: | ----: | ----: | ------:
    mBERT     | 7.53  | 1.04  | 8.24  | 41.77 | 25.46 | 8.34  | 7.30  | 14.24
    MuRIL     | 63.39 | 7.00  | 53.62 | 72.94 | 69.75 | 68.77 | 68.41 | 57.70

    <br/>

    UDPOS (F1) | hi_tr | mr_tr | ta_tr | te_tr | ur_tr | Average
    :--------- | ----: | ----: | ----: | ----: | ----: | ------:
    mBERT      | 25.00 | 33.67 | 24.02 | 36.21 | 22.07 | 28.20
    MuRIL      | 63.09 | 67.19 | 58.40 | 65.30 | 56.49 | 62.09

    <br/>

    XNLI (Accuracy) | hi_tr | ur_tr | Average
    :-------------- | ----: | ----: | ------:
    mBERT           | 39.6  | 38.86 | 39.23
    MuRIL           | 68.24 | 61.16 | 64.70

    <br/>

    Tatoeba (Accuracy) | ml_tr | ta_tr | te_tr | bn_tr | hi_tr | mr_tr | ur_tr | Average
    :----------------- | ----: | ----: | ----: | ----: | ----: | ----: | ----: | ------:
    mBERT              | 2.18  | 1.95  | 5.13  | 1.80  | 3.00  | 2.40  | 2.30  | 2.68
    MuRIL              | 10.33 | 11.07 | 11.54 | 8.10  | 14.90 | 7.20  | 13.70 | 10.98

    <br/>

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