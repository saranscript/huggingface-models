---
language: zh
widget: 
- text: "北京上个月召开了两会"

---

# Chinese RoBERTa-Base Models for Text Classification

## Model description

This is the set of 5 Chinese RoBERTa-Base classification models fine-tuned by [UER-py](https://arxiv.org/abs/1909.05658). You can download the 5 Chinese RoBERTa-Base classification models either from the [UER-py Modelzoo page](https://github.com/dbiir/UER-py/wiki/Modelzoo) (in UER-py format), or via HuggingFace from the links below:

|    Dataset     |                           Link                            |
| :-----------: | :-------------------------------------------------------: |
|  **JD full**  |   [**roberta-base-finetuned-jd-full-chinese**][jd_full]   |
| **JD binary** | [**roberta-base-finetuned-jd-binary-chinese**][jd_binary] |
| **Dianping**  |  [**roberta-base-finetuned-dianping-chinese**][dianping]  |
|   **Ifeng**   |     [**roberta-base-finetuned-ifeng-chinese**][ifeng]     |
| **Chinanews** | [**roberta-base-finetuned-chinanews-chinese**][chinanews] |

## How to use

You can use this model directly with a pipeline for text classification (take the case of roberta-base-finetuned-chinanews-chinese):

```python
>>> from transformers import AutoModelForSequenceClassification,AutoTokenizer,pipeline
>>> model = AutoModelForSequenceClassification.from_pretrained('uer/roberta-base-finetuned-chinanews-chinese')
>>> tokenizer = AutoTokenizer.from_pretrained('uer/roberta-base-finetuned-chinanews-chinese')
>>> text_classification = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)
>>> text_classification("北京上个月召开了两会")
    [{'label': 'mainland China politics', 'score': 0.7211663722991943}]
```

## Training data

5 Chinese text classification datasets are used. JD full, JD binary, and Dianping datasets consist of user reviews of different sentiment polarities. Ifeng and Chinanews consist of first paragraphs of news articles of different topic classes. They are collected by [Glyph](https://github.com/zhangxiangxiao/glyph) project and more details are discussed in corresponding [paper](https://arxiv.org/abs/1708.02657).

## Training procedure

Models are fine-tuned by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We fine-tune three epochs with a sequence length of 512 on the basis of the pre-trained model [chinese_roberta_L-12_H-768](https://huggingface.co/uer/chinese_roberta_L-12_H-768). At the end of each epoch, the model is saved when the best performance on development set is achieved. We use the same hyper-parameters on different models.

Taking the case of roberta-base-finetuned-chinanews-chinese

```
python3 run_classifier.py --pretrained_model_path models/cluecorpussmall_roberta_base_seq512_model.bin-250000 \
                          --vocab_path models/google_zh_vocab.txt \
                          --train_path datasets/glyph/chinanews/train.tsv \
                          --dev_path datasets/glyph/chinanews/dev.tsv \
                          --output_model_path models/chinanews_classifier_model.bin \
                          --learning_rate 3e-5 --batch_size 32 --epochs_num 3 --seq_length 512 \
                          --embedding word_pos_seg --encoder transformer --mask fully_visible
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_bert_text_classification_from_uer_to_huggingface.py --input_model_path models/chinanews_classifier_model.bin \
                                                                            --output_model_path pytorch_model.bin \
                                                                            --layers_num 12
```

### BibTeX entry and citation info

```
@article{devlin2018bert,
  title={BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding},
  author={Devlin, Jacob and Chang, Ming-Wei and Lee, Kenton and Toutanova, Kristina},
  journal={arXiv preprint arXiv:1810.04805},
  year={2018}
}

@article{liu2019roberta,
  title={Roberta: A robustly optimized bert pretraining approach},
  author={Liu, Yinhan and Ott, Myle and Goyal, Naman and Du, Jingfei and Joshi, Mandar and Chen, Danqi and Levy, Omer and Lewis, Mike and Zettlemoyer, Luke and Stoyanov, Veselin},
  journal={arXiv preprint arXiv:1907.11692},
  year={2019}
}

@article{zhang2017encoding,
  title={Which encoding is the best for text classification in chinese, english, japanese and korean?},
  author={Zhang, Xiang and LeCun, Yann},
  journal={arXiv preprint arXiv:1708.02657},
  year={2017}
}

@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```

[jd_full]:https://huggingface.co/uer/roberta-base-finetuned-jd-full-chinese
[jd_binary]:https://huggingface.co/uer/roberta-base-finetuned-jd-binary-chinese
[dianping]:https://huggingface.co/uer/roberta-base-finetuned-dianping-chinese
[ifeng]:https://huggingface.co/uer/roberta-base-finetuned-ifeng-chinese
[chinanews]:https://huggingface.co/uer/roberta-base-finetuned-chinanews-chinese