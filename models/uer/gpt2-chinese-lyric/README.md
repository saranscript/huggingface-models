---
language: Chinese
widget: 
- text: "最美的不是下雨天，是曾与你躲过雨的屋檐"


---


# Chinese GPT2 Lyric Model

## Model description

The model is used to generate Chinese lyrics. You can download the model either from the [GPT2-Chinese Github page](https://github.com/Morizeyao/GPT2-Chinese), or via HuggingFace from the link [gpt2-chinese-lyric](https://huggingface.co/uer/gpt2-chinese-lyric)

## How to use

You can use the model directly with a pipeline for text generation:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel, TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-chinese-lyric")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-chinese-lyric")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("最美的不是下雨天，是曾与你躲过雨的屋檐", max_length=100, do_sample=True)
    [{'generated_text': '最美的不是下雨天，是曾与你躲过雨的屋檐 ， 下 课 铃 声 响 起 的 瞬 间 ， 我 们 的 笑 脸 ， 有 太 多 回 忆 在 浮 现 ， 是 你 总 在 我 身 边 ， 不 知 道 会 不 会 再 见 ， 从 现 在 开 始 到 永 远 ， 想 说 的 语 言 凝 结 成 一 句 ， 不 管 我 们 是 否 能 够 兑 现 ， 想 说 的 语 言 凝 结'}]
```

## Training data

Training data contains 150,000 Chinese lyrics which are collected by [Chinese-Lyric-Corpus](https://github.com/gaussic/Chinese-Lyric-Corpus) and [MusicLyricChatbot](https://github.com/liuhuanyong/MusicLyricChatbot).

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 100,000 steps with a sequence length of 512 on the basis of the pre-trained model [gpt2-base-chinese-cluecorpussmall](https://huggingface.co/uer/gpt2-base-chinese-cluecorpussmall)

```
python3 preprocess.py --corpus_path corpora/lyric.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path lyric_dataset.pt --processes_num 32 \
                      --seq_length 512 --target lm
```

```
python3 pretrain.py --dataset_path lyric_dataset.pt \
                    --pretrained_model_path models/cluecorpussmall_gpt2_seq1024_model.bin-250000 \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/gpt2/config.json \
                    --output_model_path models/lyric_gpt2_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 100000 --save_checkpoint_steps 10000 --report_steps 5000 \
                    --learning_rate 5e-5 --batch_size 64 \
                    --embedding word_pos --remove_embedding_layernorm \
                    --encoder transformer --mask causal --layernorm_positioning pre \
                    --target lm --tie_weights
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_gpt2_from_uer_to_huggingface.py --input_model_path lyric_gpt2_model.bin-100000 \
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