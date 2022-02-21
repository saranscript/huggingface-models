---
language: Chinese
datasets: CLUECorpusSmall
widget: 
- text: "米饭是一种用稻米与水煮成的食物"


---


# Chinese GPT2-distil Model

## Model description

The model is used to generate Chinese texts. You can download the model either from the [GPT2-Chinese Github page](https://github.com/Morizeyao/GPT2-Chinese), or via HuggingFace from the link [gpt2-distil-chinese-cluecorpussmall](https://huggingface.co/uer/gpt2-distil-chinese-cluecorpussmall). The model is called GPT2-distil because the configuration of model follows [distilgpt2](https://huggingface.co/distilgpt2), which has 6 layers, 768 dimension, and 12 heads. The pre-training does not involve the supervision of larger models.

## How to use

You can use the model directly with a pipeline for text generation:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel, TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-distil-chinese-cluecorpussmall")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-distil-chinese-cluecorpussmall")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("这是很久之前的事情了", max_length=100, do_sample=True)
    [{'generated_text': '这是很久之前的事情了 。 我 现 在 想 起 来 就 让 自 己 很 伤 心 ， 很 失 望 。 我 现 在 想 到 ， 我 觉 得 大 多 数 人 的 生 活 比 我 的 生 命 还 要 重 要 ， 对 一 些 事 情 的 看 法 ， 对 一 些 人 的 看 法 ， 都 是 在 发 泄 。 但 是 ， 我 们 的 生 活 是 需 要 一 个 信 用 体 系 的 。 我 不 知'}]
```



## Training data

[CLUECorpusSmall](https://github.com/CLUEbenchmark/CLUECorpus2020/) is used as training data. 

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 1,000,000 steps with a sequence length of 128 and then pre-train 250,000 additional steps with a sequence length of 1024. 

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
                    --config_path models/gpt2/distil_config.json \
                    --output_model_path models/cluecorpussmall_gpt2_distil_seq128_model.bin \
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
                      --dataset_path cluecorpussmall_lm_seq1024_dataset.pt \
                      --seq_length 1024 --processes_num 32 --target lm 
```

```
python3 pretrain.py --dataset_path cluecorpussmall_lm_seq1024_dataset.pt \
                    --pretrained_model_path models/cluecorpussmall_gpt2_distil_seq128_model.bin-1000000 \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/gpt2/distil_config.json \
                    --output_model_path models/cluecorpussmall_gpt2_distil_seq1024_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 250000 --save_checkpoint_steps 50000 --report_steps 10000 \
                    --learning_rate 5e-5 --batch_size 16 \
                    --embedding word_pos --remove_embedding_layernorm \
                    --encoder transformer --mask causal --layernorm_positioning pre \
                    --target lm --tie_weights
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_gpt2_from_uer_to_huggingface.py --input_model_path cluecorpussmall_gpt2_distil_seq1024_model.bin-250000 \
                                                        --output_model_path pytorch_model.bin \
                                                        --layers_num 6
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