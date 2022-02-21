---

language: ja

license: cc-by-sa-4.0

datasets:

- YACIS corpus

---

# yacis-electra-small

This is [ELECTRA](https://github.com/google-research/electra) Small model for Japanese pretrained on 354 million sentences / 5.6 billion words of [YACIS](https://github.com/ptaszynski/yacis-corpus) blog corpus.

The corpus was tokenized for pretraining with [MeCab](https://taku910.github.io/mecab/). Subword tokenization was done with WordPiece. 

## Model architecture

This model uses ELECTRA Small model settings, 12 layers, 128 dimensions of hidden states, and 12 attention heads.

Vocabulary size was set to 32,000 tokens.

## Training data and libraries

YACIS-ELECTRA is trained on the whole of [YACIS](https://github.com/ptaszynski/yacis-corpus) blog corpus, which is a Japanese blog corpus containing 5.6 billion words in 354 million sentences.

The corpus was originally split into sentences using custom rules, and each sentence was tokenized using [MeCab](https://taku910.github.io/mecab/). Subword tokenization for pretraining was done with WordPiece. 

We used original [ELECTRA](https://github.com/google-research/electra) repository for pretraining. The pretrainig process took 7 days and 6 hours under the following environment: CPU: Intel Core i9-7920X, RAM: 132 GB, GPU: GeForce GTX 1080 Ti x1. 


## Licenses

The pretrained model with all attached files is licensed under [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/), or Creative Commons Attribution-ShareAlike 4.0 International License. 

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a>

## Citations

Please, cite the model using the following citation.

```
@inproceedings{shibata2022yacis-electra,
  title={日本語大規模ブログコーパスYACISに基づいたELECTRA事前学習済み言語モデルの作成及び性能評価}, 
%  title={Development and performance evaluation of ELECTRA pretrained language model based on YACIS large-scale Japanese blog corpus [in Japanese]}, %% for English citations
  author={柴田 祥伍 and プタシンスキ ミハウ and エロネン ユーソ and ノヴァコフスキ カロル and 桝井 文人}, 
%  author={Shibata, Shogo and Ptaszynski, Michal and Eronen, Juuso and Nowakowski, Karol and Masui, Fumito},  %% for English citations
  booktitle={言語処理学会第28回年次大会(NLP2022) (予定)}, 
%  booktitle={Proceedings of The 28th Annual Meeting of The Association for Natural Language Processing (NLP2022)},  %% for English citations
  pages={1--4},
  year={2022}
}
```


The model was build using sentences from YACIS corpus, which should be cited using at least one of the following refrences.

```
@inproceedings{ptaszynski2012yacis,
  title={YACIS: A five-billion-word corpus of Japanese blogs fully annotated with syntactic and affective information},
  author={Ptaszynski, Michal and Dybala, Pawel and Rzepka, Rafal and Araki, Kenji and Momouchi, Yoshio},
  booktitle={Proceedings of the AISB/IACAP world congress},
  pages={40--49},
  year={2012},
  howpublished = "\url{https://github.com/ptaszynski/yacis-corpus}"
}
```

```
@article{ptaszynski2014automatically,
  title={Automatically annotating a five-billion-word corpus of Japanese blogs for sentiment and affect analysis},
  author={Ptaszynski, Michal and Rzepka, Rafal and Araki, Kenji and Momouchi, Yoshio},
  journal={Computer Speech \& Language},
  volume={28},
  number={1},
  pages={38--55},
  year={2014},
  publisher={Elsevier},
  howpublished = "\url{https://github.com/ptaszynski/yacis-corpus}"
}
```