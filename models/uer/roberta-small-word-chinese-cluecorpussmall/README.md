---
language: zh
datasets: CLUECorpusSmall
widget: 
- text: "最近一趟去北京的[MASK]几点发车"



---

# Chinese word-based RoBERTa Miniatures

## Model description

This is the set of 5 Chinese word-based RoBERTa models pre-trained by [UER-py](https://github.com/dbiir/UER-py/), which is introduced in [this paper](https://arxiv.org/abs/1909.05658).

Most Chinese pre-trained weights are based on Chinese character. Compared with character-based models, word-based models are faster (because of shorter sequence length) and have better performance according to our experimental results. To this end, we released the 5 Chinese word-based RoBERTa models of different sizes. In order to facilitate users to reproduce the results, we used the publicly available corpus and word segmentation tool, and provided all training details.

Notice that the output results of Hosted inference API (right) are not properly displayed. When the predicted word has multiple characters, the single word instead of entire sentence is displayed. One can click **JSON Output** for normal output results.

You can download the 5 Chinese RoBERTa miniatures either from the [UER-py Modelzoo page](https://github.com/dbiir/UER-py/wiki/Modelzoo), or via HuggingFace from the links below:

|          |           Link           |
| -------- | :-----------------------: |
| **word-based RoBERTa-Tiny** | [**L=2/H=128 (Tiny)**][2_128] |
| **word-based RoBERTa-Mini** | [**L=4/H=256 (Mini)**][4_256] |
| **word-based RoBERTa-Small** | [**L=4/H=512 (Small)**][4_512] |
| **word-based RoBERTa-Medium** | [**L=8/H=512 (Medium)**][8_512] |
| **word-based RoBERTa-Base** | [**L=12/H=768 (Base)**][12_768] |

Compared with [char-based models](https://huggingface.co/uer/chinese_roberta_L-2_H-128), word-based models achieve better results in most cases. Here are scores on the devlopment set of six Chinese tasks:

| Model          | Score | douban | chnsenticorp | lcqmc | tnews(CLUE) | iflytek(CLUE) | ocnli(CLUE) |
| -------------- | :---: | :----: | :----------: | :---: | :---------: | :-----------: | :---------: |
| RoBERTa-Tiny(char)       | 72.3            |  83.0      |     91.4         | 81.8      |    62.0         |     55.0          |    60.3         |
| **RoBERTa-Tiny(word)**   | **74.3(+2.0)**  |  **86.4**  |     **93.2**     | **82.0**  |    **66.4**     |     **58.2**      |    **59.6**     |
| RoBERTa-Mini(char)       | 75.7            |  84.8      |     93.7         | 86.1      |    63.9         |     58.3          |    67.4         |
| **RoBERTa-Mini(word)**   | **76.7(+1.0)**  |  **87.6**  |     **94.1**     | **85.4**  |    **66.9**     |     **59.2**      |    **67.3**     |
| RoBERTa-Small(char)      | 76.8            |  86.5      |     93.4         | 86.5      |    65.1         |     59.4          |    69.7         |
| **RoBERTa-Small(word)**  | **78.1(+1.3)**  |  **88.5**  |     **94.7**     | **87.4**  |    **67.6**     |     **60.9**      |    **69.8**     |
| RoBERTa-Medium(char)     | 77.8            |  87.6      |     94.8         | 88.1      |    65.6         |     59.5          |    71.2         |
| **RoBERTa-Medium(word)** | **78.9(+1.1)**  |  **89.2**  |     **95.1**     | **88.0**  |    **67.8**     |     **60.6**      |    **73.0**     |
| RoBERTa-Base(char)       | 79.5            |  89.1      |     95.2         | 89.2      |    67.0         |     60.9          |    75.5         |
| **RoBERTa-Base(word)**   | **80.2(+0.7)**  |  **90.3**  |     **95.7**     | **89.4**  |    **68.0**     |     **61.5**      |    **76.8**     |

For each task, we selected the best fine-tuning hyperparameters from the lists below, and trained with the sequence length of 128:

- epochs: 3, 5, 8
- batch sizes: 32, 64
- learning rates: 3e-5, 1e-4, 3e-4

## How to use

You can use this model directly with a pipeline for masked language modeling (take the case of word-based RoBERTa-Medium):

```python
>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='uer/roberta-medium-word-chinese-cluecorpussmall')
>>> unmasker("[MASK]的首都是北京。")
[
    {'sequence': '中国 的首都是北京。',
     'score': 0.21525809168815613, 
     'token': 2873, 
     'token_str': '中国'}, 
    {'sequence': '北京 的首都是北京。', 
     'score': 0.15194718539714813, 
     'token': 9502, 
     'token_str': '北京'}, 
    {'sequence': '我们 的首都是北京。', 
     'score': 0.08854265511035919, 
     'token': 4215, 
     'token_str': '我们'},
    {'sequence': '美国 的首都是北京。', 
     'score': 0.06808705627918243, 
     'token': 7810, 
     'token_str': '美国'}, 
    {'sequence': '日本 的首都是北京。', 
     'score': 0.06071401759982109, 
     'token': 7788, 
     'token_str': '日本'}
]
```

Here is how to use this model to get the features of a given text in PyTorch:

```python
from transformers import AlbertTokenizer, BertModel
tokenizer = AlbertTokenizer.from_pretrained('uer/roberta-medium-word-chinese-cluecorpussmall')
model = BertModel.from_pretrained("uer/roberta-medium-word-chinese-cluecorpussmall")
text = "用你喜欢的任何文本替换我。"
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```

and in TensorFlow:

```python
from transformers import AlbertTokenizer, TFBertModel
tokenizer = AlbertTokenizer.from_pretrained('uer/roberta-medium-word-chinese-cluecorpussmall')
model = TFBertModel.from_pretrained("uer/roberta-medium-word-chinese-cluecorpussmall")
text = "用你喜欢的任何文本替换我。"
encoded_input = tokenizer(text, return_tensors='tf')
output = model(encoded_input)
```

Since BertTokenizer does not support sentencepiece, AlbertTokenizer is used here.

## Training data

[CLUECorpusSmall](https://github.com/CLUEbenchmark/CLUECorpus2020/) is used as training data. Google's [sentencepiece](https://github.com/google/sentencepiece) is used for word segmentation. The sentencepiece model is trained on CLUECorpusSmall corpus:

```
>>> import sentencepiece as spm
>>> spm.SentencePieceTrainer.train(input='cluecorpussmall.txt',
             model_prefix='cluecorpussmall_spm',
             vocab_size=100000,
             max_sentence_length=1024,
             max_sentencepiece_length=6,
             user_defined_symbols=['[MASK]','[unused1]','[unused2]',
                '[unused3]','[unused4]','[unused5]','[unused6]',
                '[unused7]','[unused8]','[unused9]','[unused10]'],
             pad_id=0,
             pad_piece='[PAD]',
             unk_id=1,
             unk_piece='[UNK]',
             bos_id=2,
             bos_piece='[CLS]',
             eos_id=3,
             eos_piece='[SEP]',
             train_extremely_large_corpus=True
            )
```

## Training procedure

Models are pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 1,000,000 steps with a sequence length of 128 and then pre-train 250,000 additional steps with a sequence length of 512. We use the same hyper-parameters on different model sizes.

Taking the case of word-based RoBERTa-Medium

Stage1:

```
python3 preprocess.py --corpus_path corpora/cluecorpussmall.txt \
                      --spm_model_path models/cluecorpussmall_spm.model \
                      --dataset_path cluecorpussmall_word_seq128_dataset.pt \
                      --processes_num 32 --seq_length 128 \
                      --dynamic_masking --target mlm
```

```
python3 pretrain.py --dataset_path cluecorpussmall_word_seq128_dataset.pt \
                    --spm_model_path models/cluecorpussmall_spm.model \
                    --config_path models/bert/medium_config.json \
                    --output_model_path models/cluecorpussmall_word_roberta_medium_seq128_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 1000000 --save_checkpoint_steps 100000 --report_steps 50000 \
                    --learning_rate 1e-4 --batch_size 64 \
                    --embedding word_pos_seg --encoder transformer --mask fully_visible --target mlm --tie_weights
```

Stage2:

```
python3 preprocess.py --corpus_path corpora/cluecorpussmall.txt \
                      --spm_model_path models/cluecorpussmall_spm.model \
                      --dataset_path cluecorpussmall_word_seq512_dataset.pt \
                      --processes_num 32 --seq_length 512 \
                      --dynamic_masking --target mlm
```

```
python3 pretrain.py --dataset_path cluecorpussmall_word_seq512_dataset.pt \
                    --pretrained_model_path models/cluecorpussmall_word_roberta_medium_seq128_model.bin-1000000 \
                    --spm_model_path models/cluecorpussmall_spm.model \
                    --config_path models/bert/medium_config.json \
                    --output_model_path models/cluecorpussmall_word_roberta_medium_seq512_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 250000 --save_checkpoint_steps 50000 --report_steps 10000 \
                    --learning_rate 5e-5 --batch_size 16 \
                    --embedding word_pos_seg --encoder transformer --mask fully_visible --target mlm --tie_weights
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_bert_from_uer_to_huggingface.py --input_model_path models/cluecorpussmall_word_roberta_medium_seq128_model.bin-250000 \
                                                        --output_model_path pytorch_model.bin \
                                                        --layers_num 8 --target mlm
```

### BibTeX entry and citation info

```
@article{devlin2018bert,
  title={BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding},
  author={Devlin, Jacob and Chang, Ming-Wei and Lee, Kenton and Toutanova, Kristina},
  journal={arXiv preprint arXiv:1810.04805},
  year={2018}
}

@article{turc2019,
  title={Well-Read Students Learn Better: On the Importance of Pre-training Compact Models},
  author={Turc, Iulia and Chang, Ming-Wei and Lee, Kenton and Toutanova, Kristina},
  journal={arXiv preprint arXiv:1908.08962v2 },
  year={2019}
}

@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```

[2_128]:https://huggingface.co/uer/roberta-tiny-word-chinese-cluecorpussmall
[4_256]:https://huggingface.co/uer/roberta-mini-word-chinese-cluecorpussmall
[4_512]:https://huggingface.co/uer/roberta-small-word-chinese-cluecorpussmall
[8_512]:https://huggingface.co/uer/roberta-medium-word-chinese-cluecorpussmall
[12_768]:https://huggingface.co/uer/roberta-base-word-chinese-cluecorpussmall