---
language: zh
widget: 
- text: "江苏警方通报特斯拉冲进店铺"

---

# Chinese RoBERTa-Base Model for NER

## Model description

The model is used for named entity recognition. You can download the model either from the [UER-py Modelzoo page](https://github.com/dbiir/UER-py/wiki/Modelzoo) (in UER-py format), or via HuggingFace from the link [roberta-base-finetuned-cluener2020-chinese](https://huggingface.co/uer/roberta-base-finetuned-cluener2020-chinese).

## How to use

You can use this model directly with a pipeline for token classification :

```python
>>> from transformers import AutoModelForTokenClassification,AutoTokenizer,pipeline
>>> model = AutoModelForTokenClassification.from_pretrained('uer/roberta-base-finetuned-cluener2020-chinese')
>>> tokenizer = AutoTokenizer.from_pretrained('uer/roberta-base-finetuned-cluener2020-chinese')
>>> ner = pipeline('ner', model=model, tokenizer=tokenizer)
>>> ner("江苏警方通报特斯拉冲进店铺")
    [
       {'word': '江', 'score': 0.49153077602386475, 'entity': 'B-address', 'index': 1, 'start': 0, 'end': 1}, 
       {'word': '苏', 'score': 0.6319217681884766, 'entity': 'I-address', 'index': 2, 'start': 1, 'end': 2}, 
       {'word': '特', 'score': 0.5912262797355652, 'entity': 'B-company', 'index': 7, 'start': 6, 'end': 7},
       {'word': '斯', 'score': 0.69145667552948, 'entity': 'I-company', 'index': 8, 'start': 7, 'end': 8}, 
       {'word': '拉', 'score': 0.7054660320281982, 'entity': 'I-company', 'index': 9, 'start': 8, 'end': 9}
    ]
```

## Training data

[CLUENER2020](https://github.com/CLUEbenchmark/CLUENER2020) is used as training data. We only use the train set of the dataset.

## Training procedure

The model is fine-tuned by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We fine-tune five epochs with a sequence length of 512 on the basis of the pre-trained model [chinese_roberta_L-12_H-768](https://huggingface.co/uer/chinese_roberta_L-12_H-768). At the end of each epoch, the model is saved when the best performance on development set is achieved.

```
python3 run_ner.py --pretrained_model_path models/cluecorpussmall_roberta_base_seq512_model.bin-250000 \
                   --vocab_path models/google_zh_vocab.txt \
                   --train_path datasets/cluener2020/train.tsv \
                   --dev_path datasets/cluener2020/dev.tsv \
                   --label2id_path datasets/cluener2020/label2id.json \
                   --output_model_path models/cluener2020_ner_model.bin \
                   --learning_rate 3e-5 --batch_size 32 --epochs_num 5 --seq_length 512 \
                   --embedding word_pos_seg --encoder transformer --mask fully_visible
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_bert_token_classification_from_uer_to_huggingface.py --input_model_path models/cluener2020_ner_model.bin \
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

@article{xu2020cluener2020,
  title={CLUENER2020: Fine-grained Name Entity Recognition for Chinese},
  author={Xu, Liang and Dong, Qianqian and Yu, Cong and Tian, Yin and Liu, Weitang and Li, Lu and Zhang, Xuanwei},
  journal={arXiv preprint arXiv:2001.04351},
  year={2020}
 }
 
@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```