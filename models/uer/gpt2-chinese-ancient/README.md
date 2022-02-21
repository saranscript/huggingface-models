---
language: Chinese
widget: 
- text: "[CLS]当是时"


---


# Chinese Ancient GPT2 Model

## Model description

The model is used to generate ancient Chinese. You can download the model either from the [GPT2-Chinese Github page](https://github.com/Morizeyao/GPT2-Chinese), or via HuggingFace from the link [gpt2-chinese-ancient](https://huggingface.co/uer/gpt2-chinese-ancient)

## How to use

You can use the model directly with a pipeline for text generation:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel, TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-chinese-ancient")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-chinese-ancient")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("当是时", max_length=100, do_sample=True)
    [{'generated_text': '[CLS]当是时 所 议 者 不 为 无 据 ， 况 亦 在 之 列 乎 ？ 然 则 今 日 之 事 ， 所 当 思 者 在 何 ？ 欲 求 国 是 于 天 下 ， 莫 在 于 得 人 。 臣 以 为 求 人 之 法 ， 不 在 多 用 官 一 途 。 诚 使 得 才 者 众 ， 人 才 者 优 ， 则 治 所 当 得 ， 而 不 事 于 官 者 ， 人 才 乃 其 常 也 。 所 当 讲 者'}]
```

## Training data

Training data contains 3,000,000 ancient Chinese which are collected by [daizhigev20](https://github.com/garychowcmu/daizhigev20). Since part of ancient corpus has no punctuation, we used the [ancient Chinese punctuation system](https://seg.shenshen.wiki) developed by [BNU ICIP lab](http://icip.bnu.edu.cn/).　


## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 500,000 steps with a sequence length of 320. We use extended vocabulary to handle out-of-vocabulary words. The Chinese character that occurs greater than or equal to 100 in ancient Chinese corpus is added to the vocabulary.

```
python3 preprocess.py --corpus_path corpora/ancient_chinese.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path ancient_chinese_dataset.pt --processes_num 16 \
                      --seq_length 320 --target lm
```

```
python3 pretrain.py --dataset_path ancient_chinese_dataset.pt \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/bert_base_config.json \
                    --output_model_path models/ancient_chinese_base_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 500000 --save_checkpoint_steps 100000 --report_steps 10000 \
                    --learning_rate 5e-4 --batch_size 32 \
                    --embedding word_pos --remove_embedding_layernorm \
                    --encoder transformer --mask causal --layernorm_positioning pre \
                    --target lm --tie_weights
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_gpt2_from_uer_to_huggingface.py --input_model_path ancient_chinese_base_model.bin-500000 \
                                                        --output_model_path pytorch_model.bin \
                                                        --layers_num 12
```

### BibTeX entry and citation info

```
@article{radford2019language,
  title={Language Models are Unsupervised Multitask Learners},
  author={Radford, Alec and Wu, Jeff and Child, Rewon and Luan, David and Amodei, Dario and Sutskever, Ilya},
  year={2019}
}

@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}

胡韧奋,李绅,诸雨辰.基于深层语言模型的古汉语知识表示及自动断句研究[C].第十八届中国计算语言学大会（CCL 2019）.
```