---

language: ja

license: cc-by-sa-4.0

datasets:

- YACIS corpus
- Harmful BBS Japanese comments dataset
- Twitter Japanese cyberbullying dataset

---

# yacis-electra-small-cyberbullying

This is an [ELECTRA](https://github.com/google-research/electra) Small model for the Japanese language finetuned for automatic cyberbullying detection. 

The original foundation model was originally pretrained on 5.6 billion words [YACIS](https://github.com/ptaszynski/yacis-corpus) blog corpus, and later finetuned on a balanced dataset created by unifying two datasets, namely "Harmful BBS Japanese comments dataset" and "Twitter Japanese cyberbullying dataset". 

## Model architecture

The original model was pretrained using ELECTRA Small model settings and can be found here:
[https://huggingface.co/ptaszynski/yacis-electra-small-japanese](https://huggingface.co/ptaszynski/yacis-electra-small-japanese)


## Licenses

The finetuned model with all attached files is licensed under [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/), or Creative Commons Attribution-ShareAlike 4.0 International License. 

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a>

## Citations

Please, cite this model using the following citation.

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

The two datasets used for finetuning should be cited using the following references.

- Harmful BBS Japanese comments dataset:
```
@book{ptaszynski2018automatic,
  title={Automatic Cyberbullying Detection: Emerging Research and Opportunities: Emerging Research and Opportunities},
  author={Ptaszynski, Michal E and Masui, Fumito},
  year={2018},
  publisher={IGI Global}
}
```
```
@article{松葉達明2009学校非公式サイトにおける有害情報検出,
  title={学校非公式サイトにおける有害情報検出},
  author={松葉達明 and 里見尚宏 and 桝井文人 and 河合敦夫 and 井須尚紀},
  journal={電子情報通信学会技術研究報告. NLC, 言語理解とコミュニケーション},
  volume={109},
  number={142},
  pages={93--98},
  year={2009},
  publisher={一般社団法人電子情報通信学会}
}
```

- Twitter Japanese cyberbullying dataset:
```
TBA
```

The pretraining was done using YACIS corpus, which should be cited using at least one of the following references.
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