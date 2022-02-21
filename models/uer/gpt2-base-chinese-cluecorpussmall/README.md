---
language: Chinese
datasets: CLUECorpusSmall
widget: 
- text: "米饭是一种用稻米与水煮成的食物"


---


<br>

**The GPT-2-base model with sequence length 1024 is available in [here](https://huggingface.co/uer/gpt2-chinese-cluecorpussmall). The model in this repository only supports sequence length 512. We will delete this repository in the near future.**

<br>


# Chinese GPT2 Model


## Model description

The model is used to generate Chinese texts. You can download the model either from the [GPT2-Chinese Github page](https://github.com/Morizeyao/GPT2-Chinese), or via HuggingFace from the link [gpt2-base-chinese-cluecorpussmall](https://huggingface.co/uer/gpt2-base-chinese-cluecorpussmall).

## How to use

You can use the model directly with a pipeline for text generation:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel, TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-base-chinese-cluecorpussmall")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-base-chinese-cluecorpussmall")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("这是很久之前的事情了", max_length=100, do_sample=True)
    [{'generated_text': '这是很久之前的事情了 ！ 这 件 事 情 之 后 我 每 天 都 问 自 己 ， 对 未 来 的 影 响 是 什 么 ？ 在 这 个 过 程 中 我 一 直 提 高 自 己 的 理 论 和 实 践 能 力 ， 比 如 说 ， 我 们 现 在 有 很 多 很 多 的 投 资 行 为 可 以 赚 钱 ， 在 美 国 有 很 多 交 易 行 为 ， 是 一 个 比 较 灵 活 的 模'}]
```



## Training data

[CLUECorpusSmall](https://github.com/CLUEbenchmark/CLUECorpus2020/) is used as training data. 

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 1,000,000 steps with a sequence length of 128 and then pre-train 250,000 additional steps with a sequence length of 512. 

Stage1:

```
python3 preprocess.py --corpus_path corpora/cluecorpussmall.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path cluecorpussmall_lm_seq128_dataset.pt \
                      --seq_length 128 --processes_num 32 --target lm 
```

```
python3 pretrain.py --dataset_path cluecorpussmall_lm_seq128_dataset.pt \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/bert_base_config.json \
                    --output_model_path models/cluecorpussmall_gpt2_seq128_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 1000000 --save_checkpoint_steps 100000 --report_steps 50000 \
                    --learning_rate 1e-4 --batch_size 64 \
                    --embedding word_pos --remove_embedding_layernorm \
                    --encoder transformer --mask causal --layernorm_positioning pre \
                    --target lm --tie_weights
```

Stage2:

```
python3 preprocess.py --corpus_path corpora/cluecorpussmall.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path cluecorpussmall_lm_seq512_dataset.pt \
                      --seq_length 512 --processes_num 32 --target lm 
```

```
python3 pretrain.py --dataset_path cluecorpussmall_lm_seq512_dataset.pt \
                    --pretrained_model_path models/cluecorpussmall_gpt2_seq128_model.bin-1000000 \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/bert_base_config.json \
                    --output_model_path models/cluecorpussmall_gpt2_seq512_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 250000 --save_checkpoint_steps 50000 --report_steps 10000 \
                    --learning_rate 5e-5 --batch_size 16 \
                    --embedding word_pos --remove_embedding_layernorm \
                    --encoder transformer --mask causal --layernorm_positioning pre \
                    --target lm --tie_weights
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_gpt2_from_uer_to_huggingface.py --input_model_path cluecorpussmall_gpt2_seq512_model.bin-250000 \
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