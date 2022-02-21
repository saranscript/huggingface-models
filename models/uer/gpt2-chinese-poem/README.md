---
language: zh 
widget:
- text: "[CLS] 万 叠 春 山 积 雨 晴 ，"
- text: "[CLS] 大 漠"

---

# Chinese Poem GPT2 Model

## Model description

The model is used to generate Chinese ancient poems. You can download the model  either from the [GPT2-Chinese Github page](https://github.com/Morizeyao/GPT2-Chinese), or via HuggingFace from the link [gpt2-chinese-poem][poem].

Since the parameter skip_special_tokens is used in the pipelines.py, special tokens such as [SEP], [UNK] will be deleted, the output results of Hosted inference API (right) may not be properly displayed.

## How to use

You can use the model directly with a pipeline for text generation:

When the parameter skip_special_tokens is True:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel,TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-chinese-poem")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-chinese-poem")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("[CLS]梅 山 如 积 翠 ，", max_length=50, do_sample=True)
    [{'generated_text': '[CLS]梅 山 如 积 翠 ， 丛 竹 隠 疏 花 。 水 影 落 寒 濑 ， 竹 声 随 暮 鸦 。 茅 茨 数 间 屋 ， 烟 火 两 三 家 。 安 得 携 琴 酒 ， 相 逢 烟 雨 赊 。 向 湖 边 过 ， 偏 怜 雪 里 看 。 浮 峦 如 画 出 ， 远 树 与 天 连 。 月 上 僧 房 静 ， 风 回 萤 火 寒 。 幽 情 何 可 写 ， 赖 有 子 期 弹 。 棠 真'}]
```

When the parameter skip_special_tokens is False:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel,TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-chinese-poem")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-chinese-poem")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("[CLS]梅 山 如 积 翠 ，", max_length=100, do_sample=True)
    [{'generated_text': '[CLS]梅 山 如 积 翠 ， 秀 出 何 其 雄 。 矫 矫 云 间 质 ， 映 日 生 玲 珑 。 根 大 乱 石 结 ， 枝 高 青 云 蒙 。 常 因 风 露 晚 ， 隠 映 瑶 台 中 。 忽 闻 山 石 裂 ， 万 里 吹 天 风 。 又 觉 此 身 高 ， 迥 出 凡 境 空 。 清 影 落 潭 水 ， 暗 香 来 逈 峰 。 却 寻 白 太 白 ， 月 影 摇 江 东 。 [SEP] 而 非'}]
```

## Training data

Training data contains 800,000 Chinese ancient poems which are collected by [chinese-poetry](https://github.com/chinese-poetry/chinese-poetry) and [Poetry](https://github.com/Werneror/Poetry) projects.

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 200,000 steps with a sequence length of 128. We use extended vocabulary to handle out-of-vocabulary words. The Chinese character that occurs greater than or equal to 100 in poem corpus is added to the vocabulary.

```
python3 preprocess.py --corpus_path corpora/poem.txt \
                      --vocab_path models/poem_zh_vocab.txt \
                      --dataset_path poem_dataset.pt --processes_num 16 \
                      --seq_length 128 --target lm 
```

```
python3 pretrain.py --dataset_path poem_dataset.pt \
                    --vocab_path models/poem_zh_vocab.txt \
                    --config_path models/gpt2/config.json \
                    --output_model_path models/poem_gpt2_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 200000 --save_checkpoint_steps 50000 --report_steps 1000 \
                    --learning_rate 5e-4 --batch_size 64 \
                    --embedding word_pos --remove_embedding_layernorm \
                    --encoder transformer --mask causal --layernorm_positioning pre \
                    --target lm --tie_weights
```

Finally, we convert the pre-trained model into Huggingface's format:
```
python3 scripts/convert_gpt2_from_uer_to_huggingface.py --input_model_path poem_gpt2_base_model.bin-200000 \
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
```

[poem]: https://huggingface.co/uer/gpt2-chinese-poem