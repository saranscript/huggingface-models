---
language: Chinese
datasets: CLUECorpusSmall
widget: 
- text: "中国的首都是[MASK]京"


---


# Chinese ALBERT

## Model description

This is the set of Chinese ALBERT models pre-trained by UER-py. You can download the model either from the [UER-py Github page](https://github.com/dbiir/UER-py/), or via HuggingFace from the links below:

|          |           Link           |
| -------- | :-----------------------: |
| **ALBERT-Base**  | [**L=12/H=768 (Base)**][base] |
| **ALBERT-Large**  | [**L=24/H=1024 (Large)**][large] |

## How to use

You can use the model directly with a pipeline for text generation:

```python
>>> from transformers import BertTokenizer, AlbertForMaskedLM, FillMaskPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/albert-base-chinese-cluecorpussmall")
>>> model = AlbertForMaskedLM.from_pretrained("uer/albert-base-chinese-cluecorpussmall")
>>> unmasker = FillMaskPipeline(model, tokenizer)   
>>> unmasker("中国的首都是[MASK]京。")
    [
        {'sequence': '中 国 的 首 都 是 北 京 。',
         'score': 0.8528032898902893, 
         'token': 1266, 
         'token_str': '北'}, 
        {'sequence': '中 国 的 首 都 是 南 京 。',
         'score': 0.07667620480060577, 
         'token': 1298, 
         'token_str': '南'}, 
        {'sequence': '中 国 的 首 都 是 东 京 。', 
         'score': 0.020440367981791496, 
         'token': 691, 
         'token_str': '东'},
        {'sequence': '中 国 的 首 都 是 维 京 。', 
         'score': 0.010197942145168781,
         'token': 5335, 
         'token_str': '维'}, 
        {'sequence': '中 国 的 首 都 是 汴 京 。', 
         'score': 0.0075391442514956, 
         'token': 3745, 
         'token_str': '汴'}
    ]

```

Here is how to use this model to get the features of a given text in PyTorch:

```python
from transformers import BertTokenizer, AlbertModel
tokenizer = BertTokenizer.from_pretrained("uer/albert-base-chinese-cluecorpussmall")
model = AlbertModel.from_pretrained("uer/albert-base-chinese-cluecorpussmall")
text = "用你喜欢的任何文本替换我。"
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```

and in TensorFlow:

```python
from transformers import BertTokenizer, TFAlbertModel
tokenizer = BertTokenizer.from_pretrained("uer/albert-base-chinese-cluecorpussmall")
model = TFAlbertModel.from_pretrained("uer/albert-base-chinese-cluecorpussmall")
text = "用你喜欢的任何文本替换我。"
encoded_input = tokenizer(text, return_tensors='tf')
output = model(encoded_input)
```

## Training data

[CLUECorpusSmall](https://github.com/CLUEbenchmark/CLUECorpus2020/) is used as training data. 

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 1,000,000 steps with a sequence length of 128 and then pre-train 250,000 additional steps with a sequence length of 512. We use the same hyper-parameters on different model sizes.

Taking the case of ALBERT-Base

Stage1:

```
python3 preprocess.py --corpus_path corpora/cluecorpussmall.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path cluecorpussmall_albert_seq128_dataset.pt \
                      --seq_length 128 --processes_num 32 --target albert 
```

```
python3 pretrain.py --dataset_path cluecorpussmall_albert_seq128_dataset.pt \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/albert/base_config.json \
                    --output_model_path models/cluecorpussmall_albert_base_seq128_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 1000000 --save_checkpoint_steps 100000 --report_steps 50000 \
                    --learning_rate 1e-4 --batch_size 64 \
                    --factorized_embedding_parameterization --parameter_sharing \
                    --embedding word_pos_seg --encoder transformer --mask fully_visible --target albert
```

Stage2:

```
python3 preprocess.py --corpus_path corpora/cluecorpussmall.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path cluecorpussmall_albert_seq512_dataset.pt \
                      --seq_length 512 --processes_num 32 --target albert 
```

```
python3 pretrain.py --dataset_path cluecorpussmall_albert_seq512_dataset.pt \
                    --pretrained_model_path models/cluecorpussmall_albert_base_seq128_model.bin-1000000 \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/albert/base_config.json \
                    --output_model_path models/cluecorpussmall_albert_base_seq512_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 1000000 --save_checkpoint_steps 100000 --report_steps 50000 \
                    --learning_rate 1e-4 --batch_size 64 \
                    --factorized_embedding_parameterization --parameter_sharing \
                    --embedding word_pos_seg --encoder transformer --mask fully_visible --target albert
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_albert_from_uer_to_huggingface.py --input_model_path cluecorpussmall_albert_base_seq512_model.bin-250000 \
                                                          --output_model_path pytorch_model.bin
```

### BibTeX entry and citation info

```
@article{lan2019albert,
  title={Albert: A lite bert for self-supervised learning of language representations},
  author={Lan, Zhenzhong and Chen, Mingda and Goodman, Sebastian and Gimpel, Kevin and Sharma, Piyush and Soricut, Radu},
  journal={arXiv preprint arXiv:1909.11942},
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
[base]:https://huggingface.co/uer/albert-base-chinese-cluecorpussmall
[large]:https://huggingface.co/uer/albert-large-chinese-cluecorpussmall